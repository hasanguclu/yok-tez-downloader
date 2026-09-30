# hsnlib
A private library of Hasan Guclu
# YÖK Tez Downloader

Small, dependency-free command-line tool for saving a **publicly available**
thesis PDF from the [YÖK National Thesis Center](https://tez.yok.gov.tr/).
It is intended for theses that the site already makes available for download;
it does not log in, retain cookies, solve CAPTCHAs, or work around access,
embargo, or copyright restrictions.

> **Use responsibly.** Download only material that YÖK has made public and
> that you are entitled to keep. Respect the thesis author's rights, the
> site's terms, and any rate limits. An embargoed or access-restricted record
> is not a bug for this tool to solve.

## Requirements

* Python 3.9 or newer
* A direct, public PDF download link on `tez.yok.gov.tr`

No third-party packages are required.

## How it works

1. Search for the record at [YÖK National Thesis Center](https://tez.yok.gov.tr/).
2. Check that the record has a public full-text/PDF download option.
3. Copy the PDF download link from the browser. The link must point to
   `tez.yok.gov.tr`; the script deliberately rejects other hosts.
4. Run the command below. The response is streamed to disk, checked for a PDF
   content type or PDF signature, then atomically moved into the output folder.

```bash
python3 yok_tez_downloader.py \
  --url 'https://tez.yok.gov.tr/.../public-download-link' \
  --output-dir theses
```

The downloader follows a small number of redirects, but every redirect must
remain on `tez.yok.gov.tr`. It uses a filename from `Content-Disposition` when
the server supplies one, otherwise it uses `yok-thesis.pdf`. It also prints a
SHA-256 checksum so the saved file can be identified later.

### Useful options

```bash
# Choose a name instead of using the server-provided name.
python3 yok_tez_downloader.py --url 'https://tez.yok.gov.tr/...' --filename thesis.pdf

# Review a URL without downloading anything.
python3 yok_tez_downloader.py --url 'https://tez.yok.gov.tr/...' --dry-run
```

Run `python3 yok_tez_downloader.py --help` for all options.

## Publishing this project on GitHub

This repository is ready to be pushed to a GitHub repository. From a clone
with GitHub authentication configured, create an empty GitHub repository and
then run:

```bash
git remote add origin git@github.com:YOUR-USER/yok-tez-downloader.git
git push -u origin work
```

Replace `work` with the branch that you want to publish. The repository's
README will be rendered automatically as its project page. If GitHub Pages is
desired, enable **Settings → Pages → Deploy from a branch**, select the branch
and `/ (root)`, and add an `index.html` tailored to the public site.

## Development

```bash
python3 -m unittest discover -s tests -v
```

## Turkish quick start (Kısa kullanım)

YÖK Tez Merkezi'nde tezin kaydını açın ve yalnızca herkese açık PDF indirme
bağlantısını kopyalayın. Ardından bağlantıyı `--url` ile programa verin.
Program giriş yapmaz veya erişim kısıtlarını aşmaya çalışmaz; erişime kapalı ya
da süreli kısıtlı tezler indirilemez.

## License

This project is released under [CC0 1.0](LICENSE).
