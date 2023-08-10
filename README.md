# test-github-action

Testing locally how to share a matrix
```bash
#wget -q https://github.com/mikefarah/yq/releases/download/v4.34.2/yq_darwin_arm64 -O yq
#chmod +x yq
cat <<EOF | yq -P -o=json - > matrix.json
matrix:
  include:
    builder-image: [ 'paketobuildpacks/builder-jammy-tiny:0.0.175' ]
    pack_cli_version: [ 'v0.30.0-rc1' ]
EOF
```

Generate matrix output
```bash
export CFG=$(cat cfg.json)
jq -r -n  'env.CFG | fromjson | @json "::set-output name=result::\(.data)"'
```

