# Jekyll 中文文档站点

此仓储包含 Jekyll 文档站点代码，[jekyllrb.com](https://jekyllrb.com/).

## 参与

For information about contributing, see the [Contributing page](https://jekyllrb.com/docs/contributing/).

## 本地运行

You can preview your contributions before opening a pull request by running from within the directory:

1. `bundle install --without test test_legacy benchmark`
2. `bundle exec rake site:preview`

It's just a jekyll site, afterall! :wink:

## 更新 Font Awesome

1. Go to <https://icomoon.io/app/>
2. Choose Import Icons and load `icomoon-selection.json`
3. Choose Generate Font → Download
4. Copy the font files and adapt the CSS to the paths we use in Jekyll
