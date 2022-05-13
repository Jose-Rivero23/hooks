# INSTALACION DE HOOKS

al finalizar proceso normal de inicio de proyecto repost.
npm i -D husky
--c---
luego

npm set-script prepare "husky install"
npm run prepare

por ultimo crear los archivos o ficheros.
npx husky add .husky/commit-msg ""
npx husky add .husky/pre-push""

se copia cada linea de codigo que hacen que los scripts queden activos

este para commits

> _------
> #!/bin/sh
> . "$(dirname "$0")/_/husky.sh"

while read line; do # Skip comments
if [ "${line:0:1}" == "#" ]; then
continue
fi
if [ ${#line} -ge 72 ] || [ ${#line} -le 10 ]; then
echo -e "\033[0;31mThe length of the message has to be between 10 and 72 characters."
exit 1
fi
done < "${1}"

exit 0

este para branch

#!/bin/sh
. "$(dirname "$0")/\_/husky.sh"

local_branch_name="$(git rev-parse --abbrev-ref HEAD)"

valid_branch_regex='^((hotfix|bugfix|feature)\/[a-zA-Z0-9\-]+)$'

message="Please check your branch name."

if [[! $local_branch_name =~ $valid_branch_regex]]; then
echo -e "\033[0;31m$message"
exit 1
fi

exit 0
<------>
