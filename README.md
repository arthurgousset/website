# Personal website

This is the source code for my personal website. It is built using [Hugo](https://gohugo.io/), a
static site generator written in Go.

## Usage

### Cloning the repository and submodules

This repository uses submodules to manage the theme and content.

Clone the repository and its submodules with:

```sh
git clone --recurse-submodules {{repository_url}}
```

where `{{repository_url}}` is the URL of this repository

For example, at the time of writing:

```sh
$ git clone --recurse-submodules git@github.com:arthurgousset/website.git
```

### Updating submodules

To update the submodules, you can run the following command:

```sh
$ git submodule update --remote
```

### Adding submodules

```sh
$ git submodule add {{repository}} [{{path}}]
```

For example:

```sh
$ git submodule add git@github.com:arthurgousset/algorithms.git content/posts/algorithms
```

### Removing submodules

```sh
$ git rm {{path}}
```

This removes the reference to the submodule in `.gitmodules`. Might still need to remove the
submodule from `.git/config` if it still shows up.

For example:

```sh
$ git rm content/posts/algorithms
```

### Running the website locally

To run the website locally, you need to have Hugo installed. You can follow the instructions on the
[Hugo website](https://gohugo.io/getting-started/installing/) to install it.

Once you have Hugo installed, you can run the following command to start the development server:

```bash
$ hugo server -D
```

### Link icons

Customise icon settings in [`render-link.html`](./layouts/_default/_markup/render-link.html).