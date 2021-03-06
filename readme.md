# Bicep Template for Running a Factorio Server in Azure Container Instances

## Prerequisites

- [Install Azure CLI](https://docs.microsoft.com/en-us/cli/azure/) (or upgrade with `az upgrade`)
- Install Bicep CLI: `az bicep install` (or upgrade with `az bicep upgrade`)

## Start/Create

```powershell
az group create --name game-servers --location centralus
az deployment group create --resource-group game-servers --template-file ./factorio.bicep --parameters location=centralus
```

## Usage

| Action              | Azure CLI Command |
| :------------------ | :---------------- |
| View container logs | `az container logs --resource-group game-servers --name factorio-{gameName}`
| Stop container      | `az container stop --resource-group game-servers --name factorio-{gameName}`
| Start container     | `az container start --resource-group game-servers --name factorio-{gameName}`
| Delete container    | `az container delete -y --resource-group game-servers --name factorio-{gameName}`

## Nuke Everything

> ⚠️⚠️⚠️ This will delete everything, include the server saves! ⚠️⚠️⚠️

```powershell
az group delete -y --name game-servers
```

## TODOs

- Split into bicep modules.
