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

```bash
python yok_tez_downloader.py

```


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
