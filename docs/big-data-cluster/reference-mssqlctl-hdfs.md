---
title: mssqlctl hdfs 参照
titleSuffix: SQL Server big data clusters
description: Mssqlctl hdfs コマンドに関する参照記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 6a2044594065e6f98ed919ace2171279e6f72c25
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67957916"
---
# <a name="mssqlctl-hdfs"></a>mssqlctl hdfs

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供する、 **hdfs**コマンド、 **mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[mssqlctl hdfs シェル](#mssqlctl-hdfs-shell) | HDFS シェルは、HDFS ファイル システムの単純な対話型コマンド シェルです。
[mssqlctl hdfs ls](#mssqlctl-hdfs-ls) | 指定されたファイルまたはディレクトリの状態を一覧表示します。
[mssqlctl hdfs が存在します](#mssqlctl-hdfs-exists) | ファイルまたはディレクトリが存在するかどうかを決定します。  True if exists の戻り値と False それ以外の場合。
[mssqlctl hdfs mkdir](#mssqlctl-hdfs-mkdir) | 指定したパスにディレクトリを作成します。
[mssqlctl hdfs mv](#mssqlctl-hdfs-mv) | 指定したファイルまたはパスを指定した場所に移動します。
[mssqlctl hdfs を作成します。](#mssqlctl-hdfs-create) | 指定した位置にテキスト ファイルを作成します。  データのパラメーターを使用して、単純なテキスト コンテンツを追加できます。
[読み取る mssqlctl hdfs](#mssqlctl-hdfs-read) | ファイルの内容を読み取る。  オフセットと長さ (バイト単位) は、省略可能なパラメーターです。
[mssqlctl hdfs rm](#mssqlctl-hdfs-rm) | ファイルまたはディレクトリを削除します。
[mssqlctl hdfs rmr](#mssqlctl-hdfs-rmr) | 再帰的には、ファイルまたはディレクトリを削除します。
[mssqlctl hdfs chmod](#mssqlctl-hdfs-chmod) | 指定したファイルまたはディレクトリのアクセス許可を変更します。
[mssqlctl hdfs chown](#mssqlctl-hdfs-chown) | 所有者または指定したファイルのグループを変更します。
## <a name="mssqlctl-hdfs-shell"></a>mssqlctl hdfs シェル
HDFS シェルは、HDFS ファイル システムの単純な対話型コマンド シェルです。
```bash
mssqlctl hdfs shell 
```
### <a name="examples"></a>使用例
シェルを起動します。
```bash
mssqlctl hdfs shell
```
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するログの詳細度を向上します。
#### `--help -h`
このヘルプ メッセージと終了を示します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv です。  既定: json。
#### `--query -q`
JMESPath クエリ文字列。 参照してください[ http://jmespath.org/ ](http://jmespath.org/])詳細と例。
#### `--verbose`
ログ記録を上げます。 完全なデバッグ ログのデバッグ - 使用します。
## <a name="mssqlctl-hdfs-ls"></a>mssqlctl hdfs ls
指定されたファイルまたはディレクトリの状態を一覧表示します。
```bash
mssqlctl hdfs ls --path -p 
                 
```
### <a name="examples"></a>使用例
状態の一覧表示
```bash
mssqlctl hdfs ls --path '/tmp'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--path -p`
リストの状態へのパス。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するログの詳細度を向上します。
#### `--help -h`
このヘルプ メッセージと終了を示します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv です。  既定: json。
#### `--query -q`
JMESPath クエリ文字列。 参照してください[ http://jmespath.org/ ](http://jmespath.org/])詳細と例。
#### `--verbose`
ログ記録を上げます。 完全なデバッグ ログのデバッグ - 使用します。
## <a name="mssqlctl-hdfs-exists"></a>mssqlctl hdfs が存在します
ファイルまたはディレクトリが存在するかどうかを決定します。  True if exists の戻り値と False それ以外の場合。
```bash
mssqlctl hdfs exists --path -p 
                     
```
### <a name="examples"></a>使用例
ファイルまたはディレクトリの存在を確認します。
```bash
mssqlctl hdfs exists --path '/tmp'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--path -p`
あるかどうかをチェックするパス。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するログの詳細度を向上します。
#### `--help -h`
このヘルプ メッセージと終了を示します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv です。  既定: json。
#### `--query -q`
JMESPath クエリ文字列。 参照してください[ http://jmespath.org/ ](http://jmespath.org/])詳細と例。
#### `--verbose`
ログ記録を上げます。 完全なデバッグ ログのデバッグ - 使用します。
## <a name="mssqlctl-hdfs-mkdir"></a>mssqlctl hdfs mkdir
指定したパスにディレクトリを作成します。
```bash
mssqlctl hdfs mkdir --path -p 
                    
```
### <a name="examples"></a>使用例
ディレクトリを作成します。
```bash
mssqlctl hdfs mkdir --path '/tmp'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--path -p`
作成するディレクトリの名前です。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するログの詳細度を向上します。
#### `--help -h`
このヘルプ メッセージと終了を示します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv です。  既定: json。
#### `--query -q`
JMESPath クエリ文字列。 参照してください[ http://jmespath.org/ ](http://jmespath.org/])詳細と例。
#### `--verbose`
ログ記録を上げます。 完全なデバッグ ログのデバッグ - 使用します。
## <a name="mssqlctl-hdfs-mv"></a>mssqlctl hdfs mv
指定したファイルまたはパスを指定した場所に移動します。
```bash
mssqlctl hdfs mv --source-path -s 
                 --target-path -t
```
### <a name="examples"></a>使用例
ファイルまたはディレクトリに移動します。
```bash
mssqlctl hdfs mv --source-path '/tmp' --target-path '/dest'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--source-path -s`
移動するディレクトリ。
#### `--target-path -t`
移動する場所。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するログの詳細度を向上します。
#### `--help -h`
このヘルプ メッセージと終了を示します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv です。  既定: json。
#### `--query -q`
JMESPath クエリ文字列。 参照してください[ http://jmespath.org/ ](http://jmespath.org/])詳細と例。
#### `--verbose`
ログ記録を上げます。 完全なデバッグ ログのデバッグ - 使用します。
## <a name="mssqlctl-hdfs-create"></a>mssqlctl hdfs を作成します。
指定した位置にテキスト ファイルを作成します。  データのパラメーターを使用して、単純なテキスト コンテンツを追加できます。
```bash
mssqlctl hdfs create --path -p 
                     --data -d
```
### <a name="examples"></a>使用例
ファイルを作成します。
```bash
mssqlctl hdfs create --path '/tmp/test.txt' --data "This is a test."
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--path -p`
作成するファイルの名前です。
#### `--data -d`
ファイルの内容。  単純なテキスト コンテンツのためのものです。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するログの詳細度を向上します。
#### `--help -h`
このヘルプ メッセージと終了を示します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv です。  既定: json。
#### `--query -q`
JMESPath クエリ文字列。 参照してください[ http://jmespath.org/ ](http://jmespath.org/])詳細と例。
#### `--verbose`
ログ記録を上げます。 完全なデバッグ ログのデバッグ - 使用します。
## <a name="mssqlctl-hdfs-read"></a>読み取る mssqlctl hdfs
ファイルの内容を読み取る。  オフセットと長さ (バイト単位) は、省略可能なパラメーターです。
```bash
mssqlctl hdfs read --path -p 
                   --offset  
                   --length -l
```
### <a name="examples"></a>使用例
ファイルの読み取り。
```bash
mssqlctl hdfs read --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--path -p`
読み取るファイルの名前。
#### `--offset`
読み取るファイル内のオフセットをバイト数。
#### `--length -l`
読み取るデータの長さ。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するログの詳細度を向上します。
#### `--help -h`
このヘルプ メッセージと終了を示します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv です。  既定: json。
#### `--query -q`
JMESPath クエリ文字列。 参照してください[ http://jmespath.org/ ](http://jmespath.org/])詳細と例。
#### `--verbose`
ログ記録を上げます。 完全なデバッグ ログのデバッグ - 使用します。
## <a name="mssqlctl-hdfs-rm"></a>mssqlctl hdfs rm
ファイルまたはディレクトリを削除します。
```bash
mssqlctl hdfs rm --path -p 
                 
```
### <a name="examples"></a>使用例
ファイルまたはディレクトリを削除します。
```bash
mssqlctl hdfs rm --path '/tmp'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--path -p`
削除するファイルの名前。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するログの詳細度を向上します。
#### `--help -h`
このヘルプ メッセージと終了を示します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv です。  既定: json。
#### `--query -q`
JMESPath クエリ文字列。 参照してください[ http://jmespath.org/ ](http://jmespath.org/])詳細と例。
#### `--verbose`
ログ記録を上げます。 完全なデバッグ ログのデバッグ - 使用します。
## <a name="mssqlctl-hdfs-rmr"></a>mssqlctl hdfs rmr
再帰的には、ファイルまたはディレクトリを削除します。
```bash
mssqlctl hdfs rmr --path -p 
                  
```
### <a name="examples"></a>使用例
再帰的なディレクトリを削除します。
```bash
mssqlctl hdfs rmr --path '/tmp'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--path -p`
再帰的に削除するファイルの名前。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するログの詳細度を向上します。
#### `--help -h`
このヘルプ メッセージと終了を示します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv です。  既定: json。
#### `--query -q`
JMESPath クエリ文字列。 参照してください[ http://jmespath.org/ ](http://jmespath.org/])詳細と例。
#### `--verbose`
ログ記録を上げます。 完全なデバッグ ログのデバッグ - 使用します。
## <a name="mssqlctl-hdfs-chmod"></a>mssqlctl hdfs chmod
指定したファイルまたはディレクトリのアクセス許可を変更します。
```bash
mssqlctl hdfs chmod --path -p 
                    --permission
```
### <a name="examples"></a>使用例
ファイルまたはディレクトリのアクセス許可を変更します。
```bash
mssqlctl hdfs chmod --permission 775 --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--path -p`
ファイルまたはアクセス許可を設定するディレクトリの名前。
#### `--permission`
設定するためのアクセス許可のオクテット。  例「775」です。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するログの詳細度を向上します。
#### `--help -h`
このヘルプ メッセージと終了を示します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv です。  既定: json。
#### `--query -q`
JMESPath クエリ文字列。 参照してください[ http://jmespath.org/ ](http://jmespath.org/])詳細と例。
#### `--verbose`
ログ記録を上げます。 完全なデバッグ ログのデバッグ - 使用します。
## <a name="mssqlctl-hdfs-chown"></a>mssqlctl hdfs chown
所有者または指定したファイルのグループを変更します。
```bash
mssqlctl hdfs chown --path -p 
                    --owner  
                    --group -g
```
### <a name="examples"></a>使用例
所有者とグループを変更します。
```bash
mssqlctl hdfs chown --owner hdfs --group superusergroup --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--path -p`
ファイルまたはディレクトリの所有者を変更するの名前。
#### `--owner`
設定する所有者の名前。
#### `--group -g`
設定するグループ名。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するログの詳細度を向上します。
#### `--help -h`
このヘルプ メッセージと終了を示します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv です。  既定: json。
#### `--query -q`
JMESPath クエリ文字列。 参照してください[ http://jmespath.org/ ](http://jmespath.org/])詳細と例。
#### `--verbose`
ログ記録を上げます。 完全なデバッグ ログのデバッグ - 使用します。

## <a name="next-steps"></a>次の手順

インストールする方法について、 **mssqlctl**ツールを参照してください[インストールの SQL Server 2019 ビッグ データ クラスターを管理する mssqlctl](deploy-install-mssqlctl.md)します。