# Redirect specs.johnosproject.it

SYSTEM repository for specs.johnosproject.it redirects.

This repo contains only a simple `index.html` file that will be published as
[GitHub Pages](https://pages.github.com/). At the same time the DNS records for
the  use the GitHub.io servers as `A` records.

So, when the user require the [http[s]://specs.johnosproject.it](https://specs.johnosproject.it)
url the DNS redirects it to the GitHub.io server where the `index.html` (or the
`404.html`) page is returned.<br/>
If the user required an `http` url, the GitHub.io server redirects it to the
`https` version of the same url.<br/>
Then, this page contains a JavaScript code that replace the `window.location`'s
protocol and domain.

That's all.


## Run

Open a browser and go to the one of the following links:
* [http://specs.johnosproject.it](http://specs.johnosproject.it)
* [https://specs.johnosproject.it](https://specs.johnosproject.it)

After some redirect it should display the [https://specs.johnosproject.org](https://specs.johnosproject.org)
page and url.


## Test

Execute the following `curl` command into a shell:

```shell
curl -v -L -o /dev/null http://specs.johnosproject.it 2>&1 | egrep -i "> Host:|> GET|* Connected|< Server|< Location|SSL:"

* Connected to specs.johnosproject.it (185.199.111.153) port 80 (#0)
> GET / HTTP/1.1
> Host: johnosproject.com
< Server: GitHub.com
< Location: https://specs.johnosproject.it/

* Connected to specs.johnosproject.it (185.199.109.153) port 443 (#1)
> GET / HTTP/2
> Host: specs.johnosproject.it
< server: GitHub.com
```

