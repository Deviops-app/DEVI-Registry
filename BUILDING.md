# Building DEVI Registry

You need the [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0) (see `global.json`).

```bash
git clone https://github.com/Deviops-app/DEVI-Registry.git
cd DEVI-Registry
dotnet restore DeviRegistry.sln
dotnet build DeviRegistry.sln --configuration Release
```

Official Windows packages remain on <https://deviops.app/tools/devi-registry/>.

See [docs/STATUS.md](docs/STATUS.md).
