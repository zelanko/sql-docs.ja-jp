---
title: DacFx と SqlPackage のリリース ノート |Microsoft Docs
description: Microsoft sqlpackage のリリース ノート。
ms.custom: tools|sos
ms.date: 02/02/2019
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: kenvh
ms.openlocfilehash: de45add2b02686f990d68f7c1c23eec385848751
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58538778"
---
# <a name="release-notes-for-sqlpackageexe"></a>SqlPackage.exe のリリース ノート

**[最新バージョンのダウンロード](sqlpackage-download.md)**

この記事では、SqlPackage.exe のリリースのバージョンによって提供される修正プログラム、機能を示します。

<!--
TODO:
The Introduction text needs to add clarity regarding the relationship between
'SqlPackage.exe' and 'DacFx' (the Microsoft 'Data-Tier Application Framework').
One added sentence would be sufficient.

Or, if there is no relationship, remove 'DacFx' from the metadata 'title:'.

I discussed this with SStein (SteveStein).
Thanks.  GeneMi (MightyPen in GitHub).  2019-03-27
-->

## <a name="181-sqlpackage"></a>18.1 sqlpackage

リリース日: &nbsp; 2019 年 2 月 1 日  
ビルド: &nbsp; 15.0.4316.1  
プレビュー リリース。

### <a name="features"></a>[機能]

| 機能 | 詳細 |
| :------ | :------ |
| UTF8 の照合順序のサポートが追加されました。 | &nbsp; |
| インデックス付きビューの非クラスター化列ストア インデックスを有効になります。 | &nbsp; |
| .NET Core 2.2 に移動します。 | &nbsp; |
| .NET Core でのスキーマ比較のメモリ ストレージを使用します。 | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>修正

| Fix | 詳細 |
| :-- | :------ |
| リバース エンジニア リングのクエリのレガシ カーディナリティ推定機能を使用するパフォーマンスが改善されました。 | &nbsp; |
| スクリプトを生成するときに、大幅なスキーマ比較のパフォーマンスの問題を修正しました。 | &nbsp; |
| 特定の拡張イベント (xevent) セッションを無視するスキーマの誤差検出ロジックを修正しました。 | &nbsp; |
| グラフ テーブルの順序を固定インポートします。 | &nbsp; |
| オブジェクトのアクセス許可を持つ外部テーブルのエクスポートを修正しました。 | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>既知の問題

このリリースには、.NET Core 2.2 を対象とする、sqlpackage のクロス プラットフォームのプレビュー ビルドが含まれています。 Sqlpackage は、macOS および Linux で実行できます。

| 既知の問題 | 詳細 |
| :---------- | :------ |
| ビルドと配置の共同作成者はサポートされていません。 | &nbsp; |
| Json データのシリアル化を使用する古い .dacpac および .bacpac ファイルはサポートされていません。 | &nbsp; |
| 参照先 .dacpacs (たとえば master.dacpac) 大文字小文字を区別するファイル システムに関する問題のため解決できません。 | (たとえばマスター参照ファイルの名前を大文字に変換を回避するには。BACPAC)。 |
| &nbsp; | &nbsp; |

## <a name="180-sqlpackage"></a>18.0 sqlpackage

リリース日: &nbsp; 2018 年 10 月 24 日  
ビルド: &nbsp; 15.0.4200.1

### <a name="features"></a>[機能]

| 機能 | 詳細 |
| :------ | :------ |
| 150 のデータベース互換性レベルのサポートが追加されました。 | &nbsp; |
| マネージ インスタンスのサポートが追加されました。 | &nbsp; |
| データベース操作の並列処理の次数を指定する MaxParallelism コマンド ライン パラメーターに追加します。 | &nbsp; |
| SQL Server に接続するときに認証トークンを指定する AccessToken コマンド ライン パラメーターに追加します。 | &nbsp; |
| ストリームの BLOB/CLOB データ型をインポートするサポートが追加されました。 | &nbsp; |
| スカラー UDF のサポートが追加されました 'INLINE' オプション。 | &nbsp; |
| グラフ テーブル 'MERGE' 構文に関するサポートが追加されました。 | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>修正

| Fix | 詳細 |
| :-- | :------ |
| 固定未解決擬似テーブルの列のグラフ。 | &nbsp; |
| データベースを作成するときに、メモリ最適化テーブルのグループを使用してメモリ最適化されたファイルを修正しました。 | &nbsp; |
| 外部テーブルの拡張プロパティを含むを修正しました。 | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="178-sqlpackage"></a>17.8 sqlpackage

リリース日: &nbsp; 2018 年 6 月 22 日  
ビルド: &nbsp; 14.0.4079.2

### <a name="features"></a>[機能]

| 機能 | 詳細 |
| :------ | :------ |
| SqlClient の例外メッセージを含む、接続エラーのエラー メッセージの改善。 | &nbsp; |
| インポート/エクスポートの 1 つのパーティション インデックスのインデックスの圧縮をサポートします。 | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>修正

| Fix | 詳細 |
| :-- | :------ |
| SQL 2017 以降のバージョンと、XML 列セットのリバース エンジニア リングの問題を修正しました。 | &nbsp; |
| 場所は Azure SQL Database の無視されましたスクリプト データベース互換性レベル 140 問題を修正しました。 | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="1741-sqlpackage"></a>17.4.1 sqlpackage

リリース日: &nbsp; 、2018 年 1 月 25 日  
ビルド: &nbsp; 14.0.3917.1

### <a name="features"></a>[機能]

| 機能 | 詳細 |
| :------ | :------ |
| 入れ子になったステートメントの数が多い TRANSACT-SQL の解析に ThreadMaxStackSize コマンド ライン パラメーターに追加します。 | &nbsp; |
| データベース カタログ照合順序のサポート。 | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>修正

| Fix | 詳細 |
| :-- | :------ |
| オンプレミス インスタンスに、Azure SQL Database .bacpac をインポートするときに、原因のエラーを修正しました。_パスワードなしのデータベース マスター _ キーは、このバージョンの SQL Server でサポートされていない_します。 | &nbsp; |
| グラフ テーブルでは、未解決の擬似列のエラーを修正しました。 | &nbsp; |
| SQL 認証を使用した、SchemaCompareDataModel を使用してスキーマを比較するを修正しました。 | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="1740-sqlpackage"></a>17.4.0 sqlpackage

リリース日: &nbsp; 2017 年 12 月 12 日  
ビルド: &nbsp; 14.0.3881.1

### <a name="features"></a>[機能]

| 機能 | 詳細 |
| :------ | :------ |
| サポートが追加されました_テンポラル リテンション期間ポリシー_ SQL 2017 + と Azure SQL Database でします。 | &nbsp; |
| 診断情報を保存するファイル パスを指定するコマンド ライン パラメーターを/DiagnosticsFile:"C:\Temp\sqlpackage.log を追加するには"。 | &nbsp; |
| 診断情報をコンソールにログインする/Diagnostics コマンド ライン パラメーターに追加します。 | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>修正

| Fix | 詳細 |
| :-- | :------ |
| データベースの互換性レベルが認識しないが発生する場合はブロックしません。 | 代わりに、最新の Azure SQL Database またはオンプレミスのプラットフォームが想定されます。 |
| &nbsp; | &nbsp; |
