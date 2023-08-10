# test-github-action

Testing locally how to share a matrix
```bash
cat <<EOF > matrix.yml
matrix:
  include:
    builder-image: [ 'paketobuildpacks/builder-jammy-tiny:0.0.175' ]
    pack_cli_version: [ 'v0.30.0-rc1' ]
EOF
yq eval -o=json matrix.yml >> re.txt
```

Generate matrix output
```bash
export CFG=$(cat cfg.json)
jq -r -n  'env.CFG | fromjson | @json "::set-output name=result::\(.data)"'
```

