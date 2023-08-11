# Test GitHub actions

Proiject aimed to test Github Workflows, actions, syntax, etc

Testing locally how to share a matrix
```bash
#wget -q https://github.com/mikefarah/yq/releases/download/v4.34.2/yq_darwin_arm64 -O yq
#chmod +x yq
json_include=$(cat <<EOF | yq -P -o=json -
include:
  builder-image: [ 'paketobuildpacks/builder-jammy-tiny:0.0.175' ]
  pack_cli_version: [ 'v0.30.0-rc1' ]
EOF
)
json_include_oneline=$(echo $json_include | jq -c . -)
echo "matrix=$json_include_oneline"
```

Generate matrix output
```bash
export CFG=$(cat cfg.json)
jq -r -n  'env.CFG | fromjson | @json "::set-output name=result::\(.data)"'
```

