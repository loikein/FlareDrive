# FlareDrive

CloudFlare R2 storage manager with Pages and Workers. Free 10 GB storage. Free serverless backend with a limit of 100,000 invocation requests per day. [More about pricing](https://developers.cloudflare.com/r2/platform/pricing/)

## Features

- Drag-and-drop upload
- Upload large files
- Create folders
- Search files
- Image/video thumbnails

## Usage

### Installation

Before starting, you should make sure that

- you have created a [CloudFlare](https://dash.cloudflare.com/) account
- your payment method is added
- R2 service is activated and at least one bucket is created

Steps:

1. Fork this project and connect your fork with CloudFlare Pages \([Deploy your site · Cloudflare Pages docs](https://developers.cloudflare.com/pages/framework-guides/deploy-anything/)\)
2. Add a custom domain \(Optional; you must make Cloudflare your nameserver to enable authentication, see below.\)
3. Bind your R2 bucket to `BUCKET` varaible
4. Manually redeploy to make R2 bindings take effect

Cloudflare pages settings:

- Framework preset: `None`
- Build command: \(empty\)
- Build output directory: \(empty\)
- Functions > R2 bucket bindings: `BUCKET` - (select your bucket from dropdown menu)

### Authentication

There is no built-in authentication support. By default everyone can read and write your storage. But CloudFlare Zero Trust can be used to protect your data. Do these steps to enable authentication: \([Enabling Access on your `*.pages.dev` domain · Cloudflare Pages docs](https://developers.cloudflare.com/pages/platform/known-issues/#enabling-access-on-your-pagesdev-domain)\)

1. Enable CloudFlare Zero Trust
2. In **Access**->**Applications**, create a self-hosted application
3. Delete the `*` from subdomain
4. Set **Path** as `api/write/` to disable public write or leave it blank to disable public read
5. Create a policy which accepts your email only

If you have added a custom domain:

1. Add the domain to Cloudflare websites. You will be given instructions to change DNS of your whole domain.
2. Follow steps 10 \~ 12 of the Enabling Access documentation.
