```bash
# For macOS arm.
curl -o deno.zip https://ghfast.top/https://github.com/denoland/deno/releases/download/v1.25.0/deno-aarch64-apple-darwin.zip
# For macOS x86.
curl -o deno.zip https://ghfast.top/https://github.com/denoland/deno/releases/download/v1.25.0/deno-x86_64-apple-darwin.zip
# For windows x86.
curl -o deno.zip https://ghfast.top/https://github.com/denoland/deno/releases/download/v1.25.0/deno-x86_64-pc-windows-msvc.zip
# For Linux x86.
curl -o deno.zip https://ghfast.top/https://github.com/denoland/deno/releases/download/v1.25.0/deno-x86_64-unknown-linux-gnu.zip

unzip deno.zip

mv deno ~/.vocal
chmod 777 ~/.vocal/deno


echo 'GITHUB_TOKEN=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' > .env
```

#### Intro

Export Discussions in a repo as `.md` files. Also generate an index of posts as well as feed (rss or json).


#### Usage (Workflow)

1. "Use this template" to create a repo for discussions
   Or create a workflow like [this](https://github.com/King-of-Infinite-Space/thoughts/blob/8cc5e57c155141d29897f6388a1605360812b18d/.github/workflows/main.yml) in an existing repo
2. Edit or overwrite  `script/config.js` as needed
3. The workflow will run automatically when a discussion is created or edited

#### Usage (Local)

1. Install deno (developed on `1.25`)
2. Set environment variable [`GITHUB_TOKEN`](https://github.com/settings/tokens) in command line or in `.env` file in project directory
3. Edit `script/config.js` as needed
4. `deno run --allow-net --allow-env --allow-read --allow-write scripts/fetchPosts.js`

#### Background

Some projects (e.g. [YeungKC/Hakuba](https://github.com/YeungKC/Hakuba)) use *Github Discussions* as a Content Management System for blogs. (In fact, *Github Discussions* works very well as a blog by itself.) Basically, the workflows of those projects are

1. Export discussions to `.md` files
2. Use static site generator to build `.html` pages

This project only does 1. Then the files can be used for any SSG or just as backup. The generated feed can be used by a feed reader ([demo link](https://cdn.jsdelivr.net/gh/King-of-Infinite-Space/gh-discussions-export/demo_output/feed.rss)).
