bin/Release/net8.0/MyFirstKubewardenPolicy.wasm: MyFirstKubewardenPolicy.csproj *.cs
	dotnet build -c Release

annotated-policy.wasm: bin/Release/net8.0/MyFirstKubewardenPolicy.wasm
	kwctl annotate -m metadata.yml -o annotated-policy.wasm bin/Release/net8.0/MyFirstKubewardenPolicy.wasm

.PHONY: e2e-tests
e2e-tests: annotated-policy.wasm
	bats e2e.bats

.PHONY: clean
clean:
	rm -rf bin obj annotated-policy.wasm
