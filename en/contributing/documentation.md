# Contributing to Documentation

Making quick fixes to existing text or raising issues is very easy.
More complicated changes will require you to set up the [Gitbook toolchain](https://github.com/GitbookIO/gitbook/blob/master/docs/setup.md).
If you want to help, [get in touch](../README.md#getting-help).

> **Tip** You will need a [Github](https://github.com/) login to make and submit changes to this guide.

## Overview

This guide is written in [markdown](https://github.com/GitbookIO/gitbook/blob/master/docs/syntax/markdown.md) wiki syntax and stored in the Github [mavlink/MAVSDK-docs](https://github.com/mavlink/MAVSDK-docs) repo.
The book is hosted on [Gitbook.com](https://www.gitbook.com/) and is automatically rebuilt whenever the master branch of the repo is updated.
You can also rebuild it locally using the [Gitbook toolchain](https://github.com/GitbookIO/gitbook/blob/master/docs/setup.md).

The [API Reference](../api_reference/README.md) section is compiled from source code into markdown using a [separate toolchain](#api-reference) and then copied into Github.
Updates to the reference should be made in the [source code repository](https://github.com/mavlink/MAVSDK) (see [API Reference](#api-reference) below for more information).

The guide is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) - if you make any changes then they will be made available under the same license. 


## Making a Quick Fix

Simple fixes to an existing page can be made directly on Github:

1. Click the **Edit** button in the top toolbar to open the page

   ![Edit page](../../assets/site/gitbook_toolbar_edit.png)
   
1. Make required changes in the editor section near the top of the page.
2. At the bottom of the page, add a comment and select the second radio button to create a new branch.

   ![Edit page](../../assets/site/github_edit.png)

3. Follow the on-screen instructions to create a pull request with your change.


## Raising an Issue

To raise an issue against the documentation:

1. Open the page with problem content.
1. Click the **Bug** button in the top toolbar.

   ![Raise bug](../../assets/site/gitbook_toolbar_bug.png)
   
   This will open a bug in Github, seeded with the URL/name for the current page. 
1. Enter enough information for someone to understand the problem, and ideally to fix it. 


## Making a Big Change

If you want to make more significant changes or additions to the documentation you will need to set up *Git* and the *Gitbook* toolchain (this allows you to render the documentation and check that links work). 

For setup information see: [Gitbook toolchain](https://github.com/GitbookIO/gitbook/blob/master/docs/setup.md).


## API Reference

The C++ source code is annotated using comments using [Doxygen](http://doxygen.nl/manual/index.html) syntax. 
You can extract the documentation to markdown files (one per class) on macOS or Linux using the instructions in [Building SDK from Source > Build API Reference Documentation](../contributing/build.md#build_api_reference).

In order to include new API reference in the *SDK Documentation* it must be manually added to the [Github repository](https://github.com/mavlink/MAVSDK-docs):
- Copy the files into the [/en/api_reference](https://github.com/mavlink/MAVSDK-docs/tree/{{ book.github_branch }}/en/api_reference) folder
- *New* APIs should be added to appropriate sections in the [MAVSDK-docs/en/SUMMARY.md](https://github.com/mavlink/MAVSDK-docs/blob/{{ book.github_branch }}/en/SUMMARY.md) and [/en/api_reference/README.md](https://github.com/mavlink/MAVSDK-docs/blob/{{ book.github_branch }}/en/api_reference/README.md).
