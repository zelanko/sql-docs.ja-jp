---
title: Microsoft の DacFx & sqlpackage のリリース ノート |Microsoft Docs
description: Microsoft sqlpackage のリリース ノート
ms.custom: tools|sos
ms.date: 06/20/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: kenvh
ms.openlocfilehash: f9fe0558b169acea58bb98a4f9a07267549aa58f
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56013003"
---
# <a name="sqlpackage-release-notes"></a>sqlpackage のリリース ノート

**[最新バージョンのダウンロード](sqlpackage-download.md)**

## <a name="sqlpackage-181"></a>sqlpackage 18.0

リリース日:2009 年 2 月 1 日  
ビルド13.0.0.0 

リリースには、次の機能と修正プログラムが含まれています。

- UTF8 の照合順序のサポートが追加されました。
- リバース エンジニア リングのクエリのレガシ カーディナリティ推定機能を使用するパフォーマンスが改善されました。
- インデックス付きのビューの非クラスター化列ストア インデックスを有効になります。
- スクリプトを生成するときに、大幅なスキーマ比較のパフォーマンスの問題を修正しました。
- 特定の xevent セッションを無視するスキーマの誤差検出ロジックを修正しました。
- グラフ テーブルの順序を固定インポートします。
- オブジェクトのアクセス許可を持つ外部テーブルのエクスポートを修正しました。
- .NET Core 2.2 へ移動 
- .NET Core でのスキーマ比較のメモリ ストレージを使用します。

このリリースではクロス プラットフォームのプレビュー ビルド sqlpackage を対象に .NET Core 2.2、および macOS および Linux で実行できます。 このプレビュー リリースには、次の既知の問題があります。

- ビルドと配置の共同作成者はサポートされていません。
- Json データのシリアル化を使用する古い .dacpac および .bacpac ファイルはサポートされていません。
- 参照先 .dacpacs (たとえば master.dacpac) 大文字小文字を区別するファイル システムに関する問題のため解決できません。
  - (たとえばマスター参照ファイルの名前を大文字に変換を回避するには。BACPAC)。
## <a name="sqlpackage-180"></a>sqlpackage 18.0

リリース日:2018 年 10 月 24 日  
ビルド15.0.4200.1 

リリースには、次の機能と修正プログラムが含まれています。

- 150 のデータベース互換性レベルのサポートが追加されました。
- マネージ インスタンスのサポートが追加されました。
- データベース操作の並列処理の次数を指定する MaxParallelism コマンド ライン パラメーターに追加します。
- SQL Server に接続するときに認証トークンを指定する AccessToken コマンド ライン パラメーターを追加します。
- ストリームの BLOB/CLOB データ型をインポートするサポートが追加されました。
- スカラー UDF のサポートが追加されました 'INLINE' オプション。
- グラフ テーブル 'MERGE' 構文に関するサポートが追加されました。
- 固定未解決擬似テーブルの列のグラフ。
- データベースを作成するときに、メモリ最適化テーブルのグループを使用してメモリ最適化されたファイルを修正しました。
- 外部テーブルの拡張プロパティを含むを修正しました。

## <a name="sqlpackage-178"></a>sqlpackage 17.8

リリース日:2018 年 6 月 4 日  
ビルド14.0.4079.2  

このリリースでは、次の問題点を修正しました。

- SqlClient の例外メッセージを含む、接続エラーのエラー メッセージの改善。
- インポート/エクスポートの 1 つのパーティション インデックスのインデックスの圧縮をサポートします。
- SQL 2017 以降のバージョンと、XML 列セットのリバース エンジニア リングの問題を修正しました。
- 場所は Azure SQL Database の無視されましたスクリプト データベース互換性レベル 140 問題を修正しました。

## <a name="sqlpackage-1741"></a>sqlpackage 17.4.1

リリース日:2018 年 1 月 25 日  
ビルド14.0.3917.1

このリリースでは、次の問題点を修正しました。

- オンプレミス インスタンスに、Azure SQL Database .bacpac をインポートするときに、'SQL Server のこのバージョンでは、パスワードを指定せず、データベース マスター _ キーはサポートされていません' に起因するエラーを修正しました。
- データベース カタログ照合順序のサポート。
- グラフ テーブルでは、未解決の擬似列のエラーを修正しました。
- 入れ子になったステートメントの数が多い TSQL を解析する ThreadMaxStackSize コマンド ライン パラメーターに追加します。
- SQL 認証を使用した、SchemaCompareDataModel を使用してスキーマを比較するを修正しました。

## <a name="sqlpackage-1740"></a>sqlpackage 17.4.0

リリース日:2019 年 12 月 12日  
ビルド13.0.0.0

このリリースでは、次の問題点を修正しました。

- 理解しないデータベースの互換性レベルが発生した場合はブロックしません。 代わりに、最新の Azure SQL Database またはオンプレミス プラットフォームが想定されます。
- SQL2017 + と Azure SQL Database でテンポラル リテンション期間ポリシーのサポートが追加されました。
- 診断情報を保存するファイル パスを指定するコマンド ライン パラメーターを/DiagnosticsFile:"C:\Temp\sqlpackage.log を追加するには"。
- 診断情報をコンソールにログインする/Diagnostics コマンド ライン パラメーターに追加します。

