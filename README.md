# ion-fusion.github.io
Source of org-level GitHub Pages

## Local Development

On Mac, you'll need to install Ruby via Homebrew:

```shell
brew install ruby
```

...and add it to your path:

```shell
PATH=/opt/homebrew/opt/ruby/bin:$PATH
```

(I like to use `direnv` for the latter, so it's a local configuration.)


### After checkout

```shell
bundle install
```


### Serve the Site Locally

```shell
bundle exec jekyll serve
```

Pleasantly, the server will regenerate content when pages change.

For more info, see
[Testing your GitHub Pages site locally with Jekyll](https://docs.github.com/en/articles/testing-your-github-pages-site-locally-with-jekyll).


### Deploying your fork to GitHub Pages

You _can_ enable GitHub Pages deployments on your fork, but the site will be broken.
That's because the URLs GitHub uses for account-level and repo-level Pages are incompatible 
as far as Jekyll is concerned. Here, the upstream repo will deploy to `ion-fusion.github.io`
due to it having that magic name. But when forked, it'll deploy to (eg) 
`toddjonker.github.io/ion-fusion.github.io` which breaks all relative links unless the Jekyll
config is tweaked. I don't have a great solution to this, but we can probably live without it
and rely on local debugging.

To fix this, you'll need to create a local branch in which you change this setting in
`_config.yml`:

```yaml
baseurl: "/ion-fusion.github.io"   # ...or whatever you've named your fork
```

Push that branch to GitHub, and configure your repo's Pages to publish from that branch.

**Be very careful not to propagate that change upstream!**

Surprisingly, I could only find two complaints about this problem:

* https://stackoverflow.com/questions/46177672 notes the above change, along with
  a CNAME change that I've yet to need (but probably will).
* https://github.com/actions/starter-workflows/issues/1673 links to code that seems
  to address the problem, but its from an obsolete workflow version. And that approach
  doesn’t cover the older “publish from a branch” approach I’m currently using.
