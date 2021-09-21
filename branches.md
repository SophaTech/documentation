# Como funciona

Existem duas branches principais que são responsáveis pelo ambiente de produção e staging, sendo elas respectivamente a master e dev. A master só receberá pull requests da branch dev, já as branch dev será responsável por receber pull requests das branches com prefixo feature/ e fix/.

## Criação de branches

Antes de criar qualquer branch, atualize sua branch master local, seguindo este fluxo:

```shell
git remote update -p
```
```shell
git checkout master
```
```shell
git reset --hard origin/master
```

## Prefixo das branches

### Feature

Cada nova funcionalidade deve residir na própria branch com prefixo feature/ sendo ramificada a partir da master.
Quando uma funcionalidade é concluída, ela é mesclada de volta na branch com prefixo release/ de mesmo sufixo. As funcionalidades não devem nunca interagir direto com a branch master.

### Hotfix

As branches com prefixo hotfix/ são usadas para corrigir com rapidez problemas de produção. Elas são baseadas a partir da branch master e assim que a correção é concluída, ela deve ser mesclada diretamente na branch master.

### Fix

As branches com prefixo fix/ são usadas para corrigir problemas de produção que não exija/consiga ser corrigidos com rapidez. As branches fix/ são ramificadas a partir da branch master e assim que a correção é concluída, ela deve ser mesclada para a branch dev.

### Sufixo das branches

O sufixo das branches seguira o seguinte modelo SOPHA-numero-da-issue-titulo-da-issue, por exemplo SOPHA-201-create-project-validation, sendo assim prefixo+sufixo:
feature/SOPHA-201-create-project-validation

## Atualização das branches localmente

Ao trabalhar com uma issue, todos os dias antes de iniciar o dia de trabalho, baixe as atualizações da branch master e faça o rebase para a branch da sua issue, seguindo este fluxo:

```shell
git remote update -p
```
```shell
git checkout nome_da_branch_da_issue
```
```shell
git pull origin/master --rebase
```
