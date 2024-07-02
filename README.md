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

### Running the website locally

To run the website locally, you need to have Hugo installed. You can follow the instructions on the
[Hugo website](https://gohugo.io/getting-started/installing/) to install it.

Once you have Hugo installed, you can run the following command to start the development server:

```bash
$ hugo server -D
```