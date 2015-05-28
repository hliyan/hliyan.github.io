---
layout: post
title: Jekyll post script
date: 2015-05-28 11:51:18
---
I copied and adapted this simple [script](https://github.com/tlatsas/utils-scripts/blob/master/jekyll-post) by [tlatsas](https://github.com/tlatsas) for creating new Jekyll posts. This post was created using this very script.

~~~ bash
#!/bin/bash

if [[ -z $1 ]]; then
    echo "A post title is required. Bye.."
    exit 1
fi

EDITOR='focuswriter'
_post=$(echo $1 | tr ' ' '-')
_date=$(date +'%Y-%m-%d')
_datetime=$(date +'%Y-%m-%d %H:%M:%S')
_title="${_date}-${_post}.md"
_cwd=$(pwd)'/_posts'
_post_file="${_cwd}/${_title}"

if [[ -f ${_post_file} ]]; then
    echo "File already exists. Bye.."
    exit 1
fi

cat << EOF >| ${_post_file}
---
layout: post
title: $1
date: $_datetime
---
EOF

echo 'File created successfully.'
echo

${EDITOR} ${_post_file}

echo -n 'Post? y/n : '
read answer
if [[ "${answer}" == 'n' || "${answer}" == 'N' ]]; then
    exit 0
else
    git add .
    git commit -m post
    git push
fi

exit 0
~~~