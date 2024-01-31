---
layout: post
title:  "Just delete node_modules and package-lock.json! npm install vs npm clean-install"
date:   2024-02-1 19:55:06 +0200
categories: jekyll update
---
`npm install` and `npm clean-install` are two different commands used in Node.js projects to manage dependencies defined in the package.json file. They have distinct behaviors:
- `npm install`: This is the most commonly used command to install dependencies in a Node.js project. It reads the package.json file and installs the required packages listed under dependencies and devDependencies. If a `package-lock.json` or `npm-shrinkwrap.json` file exists, it will install dependencies as specified in those files to ensure consistency across installations. However, if there are newer versions of dependencies that satisfy the version ranges specified in `package.json`, `npm install` might update `package-lock.json` with these newer versions.

- `npm clean-install` (`npm ci`): This command is designed for automated environments such as continuous integration pipelines. It requires both `package.json` and `package-lock.json` or `npm-shrinkwrap.json` files to be present. The key difference is that `npm ci` will delete the existing `node_modules` directory and install the dependencies exactly as specified in `package-lock.json` or `npm-shrinkwrap.json`, ignoring what's in `package.json`. This ensures a clean, consistent installation of dependencies as per the lock file, without any updates or changes. It's faster than npm install as it skips certain user-friendly features and is more strict in how it handles the installation process.

In summary, while npm install is suitable for development environments where you might want the latest updates of dependencies within specified version ranges, npm `clean-install` (or `npm ci`) is better for automated environments where you need to ensure consistent, repeatable builds using exact versions of dependencies.

