---
title: azdata bdc hdfs リファレンス
titleSuffix: SQL Server big data clusters
description: Azdata bdc hdfs コマンドのリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 8e892c2d501902ef915a297440ae5a6ffda83bce
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426182"
---
# <a name="azdata-bdc-hdfs"></a>azdata bdc hdfs

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事では、 **azdata**ツールでの**bdc hdfs**コマンドのリファレンスを示します。 その他の**azdata**コマンドの詳細については、「 [azdata reference](reference-azdata.md)」を参照してください。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[azdata bdc hdfs シェル](#azdata-bdc-hdfs-shell) | HDFS シェルは、HDFS ファイルシステム用の単純な対話型コマンドシェルです。
[azdata bdc hdfs ls](#azdata-bdc-hdfs-ls) | 指定されたファイルまたはディレクトリの状態を一覧表示します。
[azdata bdc hdfs が存在します](#azdata-bdc-hdfs-exists) | ファイルまたはディレクトリが存在するかどうかを確認します。  Exists の場合は True、それ以外の場合は False を返します。
[azdata bdc hdfs mkdir](#azdata-bdc-hdfs-mkdir) | 指定したパスにディレクトリを作成します。
[azdata bdc hdfs mv](#azdata-bdc-hdfs-mv) | 指定したファイルまたはパスを指定した場所に移動します。
[azdata bdc hdfs の作成](#azdata-bdc-hdfs-create) | 指定した場所にテキストファイルを作成します。  単純なテキストコンテンツは、データパラメーターを使用して追加できます。
[azdata bdc hdfs cat](#azdata-bdc-hdfs-cat) | ファイルの内容を読み取ります。  オフセットとバイト単位の長さは省略可能なパラメーターです。
[azdata bdc hdfs rm](#azdata-bdc-hdfs-rm) | ファイルまたはディレクトリを削除します。
[azdata bdc hdfs rmr](#azdata-bdc-hdfs-rmr) | ファイルまたはディレクトリを再帰的に削除します。
[azdata bdc hdfs chmod](#azdata-bdc-hdfs-chmod) | 指定されたファイルまたはディレクトリに対するアクセス許可を変更します。
[azdata bdc hdfs chown](#azdata-bdc-hdfs-chown) | 指定されたファイルの所有者またはグループを変更します。
[azdata bdc hdfs のマウント](reference-azdata-bdc-hdfs-mount.md) | HDFS 内のリモートストアのマウントを管理します。
## <a name="azdata-bdc-hdfs-shell"></a>azdata bdc hdfs シェル
HDFS シェルは、HDFS ファイルシステム用の単純な対話型コマンドシェルです。
```bash
azdata bdc hdfs shell 
```
### <a name="examples"></a>使用例
シェルを起動します。
```bash
azdata bdc hdfs shell
```
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-hdfs-ls"></a>azdata bdc hdfs ls
指定されたファイルまたはディレクトリの状態を一覧表示します。
```bash
azdata bdc hdfs ls --path -p 
                   
```
### <a name="examples"></a>使用例
状態の一覧表示
```bash
azdata bdc hdfs ls --path '/tmp'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--path -p`
状態を一覧表示するパス。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-hdfs-exists"></a>azdata bdc hdfs が存在します
ファイルまたはディレクトリが存在するかどうかを確認します。  Exists の場合は True、それ以外の場合は False を返します。
```bash
azdata bdc hdfs exists --path -p 
                       
```
### <a name="examples"></a>使用例
ファイルまたはディレクトリが存在するかどうかを確認します。
```bash
azdata bdc hdfs exists --path '/tmp'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--path -p`
存在を確認するためのパス。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-hdfs-mkdir"></a>azdata bdc hdfs mkdir
指定したパスにディレクトリを作成します。
```bash
azdata bdc hdfs mkdir --path -p 
                      
```
### <a name="examples"></a>使用例
ディレクトリを作成します。
```bash
azdata bdc hdfs mkdir --path '/tmp'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--path -p`
作成するディレクトリの名前。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-hdfs-mv"></a>azdata bdc hdfs mv
指定したファイルまたはパスを指定した場所に移動します。
```bash
azdata bdc hdfs mv --source-path -s 
                   --target-path -t
```
### <a name="examples"></a>使用例
ファイルまたはディレクトリを移動します。
```bash
azdata bdc hdfs mv --source-path '/tmp' --target-path '/dest'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--source-path -s`
移動するディレクトリ。
#### `--target-path -t`
移動先の場所。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-hdfs-create"></a>azdata bdc hdfs の作成
指定した場所にテキストファイルを作成します。  単純なテキストコンテンツは、データパラメーターを使用して追加できます。
```bash
azdata bdc hdfs create --path -p 
                       --data -d
```
### <a name="examples"></a>使用例
ファイルを作成します。
```bash
azdata bdc hdfs create --path '/tmp/test.txt' --data "This is a test."
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--path -p`
作成するファイルの名前。
#### `--data -d`
ファイルの内容。  単純なテキストコンテンツを対象としています。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-hdfs-cat"></a>azdata bdc hdfs cat
ファイルの内容を読み取ります。  オフセットとバイト単位の長さは省略可能なパラメーターです。
```bash
azdata bdc hdfs cat --path -p 
                    --offset  
                    --length -l
```
### <a name="examples"></a>使用例
ファイルを読み取ります。
```bash
azdata bdc hdfs cat --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--path -p`
読み取るファイルの名前。
#### `--offset`
読み取るファイル内のオフセットバイト数。
#### `--length -l`
読み取るデータの長さ。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-hdfs-rm"></a>azdata bdc hdfs rm
ファイルまたはディレクトリを削除します。
```bash
azdata bdc hdfs rm --path -p 
                   
```
### <a name="examples"></a>使用例
ファイルまたはディレクトリを削除します。
```bash
azdata bdc hdfs rm --path '/tmp'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--path -p`
削除するファイルの名前。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-hdfs-rmr"></a>azdata bdc hdfs rmr
ファイルまたはディレクトリを再帰的に削除します。
```bash
azdata bdc hdfs rmr --path -p 
                    
```
### <a name="examples"></a>使用例
ディレクトリを再帰的に削除します。
```bash
azdata bdc hdfs rmr --path '/tmp'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--path -p`
再帰的に削除するファイルの名前。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-hdfs-chmod"></a>azdata bdc hdfs chmod
指定されたファイルまたはディレクトリに対するアクセス許可を変更します。
```bash
azdata bdc hdfs chmod --path -p 
                      --permission
```
### <a name="examples"></a>使用例
ファイルまたはディレクトリのアクセス許可を変更します。
```bash
azdata bdc hdfs chmod --permission 775 --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--path -p`
アクセス許可を設定するファイルまたはディレクトリの名前。
#### `--permission`
設定するアクセス許可のオクテット。  例 "775"。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-hdfs-chown"></a>azdata bdc hdfs chown
指定されたファイルの所有者またはグループを変更します。
```bash
azdata bdc hdfs chown --path -p 
                      --owner  
                      --group -g
```
### <a name="examples"></a>使用例
所有者とグループを変更します。
```bash
azdata bdc hdfs chown --owner hdfs --group superusergroup --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--path -p`
所有者を変更するファイルまたはディレクトリの名前。
#### `--owner`
に設定する所有者の名前。
#### `--group -g`
に設定するグループ名。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。

## <a name="next-steps"></a>次の手順

その他の**azdata**コマンドの詳細については、「 [azdata reference](reference-azdata.md)」を参照してください。 **Azdata**ツールをインストールする方法の詳細については、「 [Azdata をインストールして SQL Server 2019 ビッグデータクラスターを管理する](deploy-install-azdata.md)」を参照してください。
