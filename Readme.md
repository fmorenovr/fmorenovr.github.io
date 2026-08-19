# Personal resume website

See the website [here](https://resume.fmorenovr.com/).

# Pre Requisites

* **GEM** >= 3.3.5
* **ruby** >= 3.0.2p107
* **bundle** >= 2.5.9
* **quarto** >= 1.6.42

# Setting up locally

Install ruby and gem:

```bash
sudo apt install jekyll
sudo apt-get install ruby ruby-dev make gcc
sudo apt-get install rubygems-integration
```

Install gem dependencies:

```bash
sudo gem install just-the-docs
sudo gem install json -v '2.9.1'
sudo gem install forwardable-extended colorator http_parser.rb eventmachine pathutil kramdown sass-embedded jekyll-sass-converter em-websocket i18n ffi rb-inotify listen jekyll-watch jekyll jekyll-include-cache jekyll-seo-tag bigdecimal google-protobuf
```

Then, install components:

```bash
bundle install
```

Finally, serve:

```bash
bundle exec jekyll serve
```
