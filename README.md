# cicd
making a simple cicd


## Instructions
- identify the main package path/directory where you will be running build and releasing from
- .github\workflows\ci-cd.yml
    - set default>run>working-directory to the main path
- main_path/release.config.json
    - move this file to the main path

- set up node npm project
- npm install --save-dev semantic-release @semantic-release/changelog @semantic-release/git @semantic-release/npm

- (optional) setup commitlint (npm i husky @commitlint/cli @commitlint/config-conventional)
\\.husky\pre-commit
```
#!/usr/bin/env sh
. "$(dirname -- "$0")/_/husky.sh"

npx lint-staged
```

set up deployment
note that vite puts files at dist while create-react-app puts them at /build

netlify:
add netlify keys to github repo
NETLIFY_AUTH_TOKEN
NETLIFY_SITE_ID

stop preview and production builds by netlify:
- Go to Site configuration > Build & deploy > Continuous deployment > Branches and deploy contexts. Set Deploy Previews to Disabled.
- Stop all builds: Go to Build settings > Stop builds.

set build-dir in the workflows to the full path, i.e. root/project/build (relative didn't work for me).


