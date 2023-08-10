# test-github-action

Testing locally how to share a matrix
```bash
cat <<EOF > cfg.yml
data:
 - { builder-image: paketobuildpacks/builder-jammy-tiny:0.0.175 }
 - { builder-image: paketobuildpacks/builder-jammy-tiny:0.0.173 }
 #- { go: 1.13, commit: v1.0.0 }
 #- { go: 1.14, commit: v1.2.0 }
EOF

yq -o=json cfg.yml > cfg.json 
```

Generate matrix output
```bash
export CFG=$(cat cfg.json)
jq -r -n  'env.CFG | fromjson | @json "::set-output name=result::\(.data)"'
```

