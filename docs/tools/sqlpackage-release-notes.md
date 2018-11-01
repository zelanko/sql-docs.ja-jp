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
ms.openlocfilehash: 55df71c62fddfe6d21abb27235b287963b946709
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47754336"
---
# <a name="sqlpackage-release-notes"></a>sqlpackage のリリース ノート

**[最新バージョンのダウンロード](sqlpackage-download.md)**

## <a name="sqlpackage-178"></a>sqlpackage 17.8

リリース日: 2018 年 6 月 22 日  
ビルド: 14.0.4079.2  

このリリースでは、次の問題点を修正しました。

- SqlClient の例外メッセージを含む、接続エラーのエラー メッセージの改善。
- データベース操作の並列処理の次数を指定する MaxParallelism コマンド ライン パラメーターに追加します。
- インポート/エクスポートの 1 つのパーティション インデックスのインデックスの圧縮をサポートします。
- SQL 2017 以降のバージョンと、XML 列セットのリバース エンジニア リングの問題を修正しました。
- 場所は Azure SQL Database の無視されましたスクリプト データベース互換性レベル 140 問題を修正しました。

## <a name="sqlpackage-1741"></a>sqlpackage 17.4.1

リリース日: 2018 年 1 月 25 日  
ビルド: 14.0.3917.1

このリリースでは、次の問題点を修正しました。

- オンプレミス インスタンスに、Azure SQL Database .bacpac をインポートするときに、'SQL Server のこのバージョンでは、パスワードを指定せず、データベース マスター _ キーはサポートされていません' に起因するエラーを修正しました。
- データベース カタログ照合順序のサポート。
- グラフ テーブルでは、未解決の擬似列のエラーを修正しました。
- 入れ子になったステートメントの数が多い TSQL を解析する ThreadMaxStackSize コマンド ライン パラメーターに追加します。
- SQL 認証を使用した、SchemaCompareDataModel を使用してスキーマを比較するを修正しました。

## <a name="sqlpackage-1740"></a>sqlpackage 17.4.0

リリース日: 2017 年 12 月 12 日  
ビルド: 14.0.3881.1

このリリースでは、次の問題点を修正しました。

- 理解しないデータベースの互換性レベルが発生した場合はブロックしません。 代わりに、最新の Azure SQL Database またはオンプレミス プラットフォームが想定されます。
- SQL2017 + と Azure SQL Database でテンポラル リテンション期間ポリシーのサポートが追加されました。
- 診断情報を保存するファイル パスを指定するコマンド ライン パラメーターを/DiagnosticsFile:"C:\Temp\sqlpackage.log を追加するには"。
- 診断情報をコンソールにログインする/Diagnostics コマンド ライン パラメーターに追加します。

## <a name="sqlpackage-on-macos-and-linux-001-preview"></a>macOS および Linux 0.0.1 (プレビュー) で sqlpackage

リリース日: 2018 年 5 月 9 日  
ビルド: 15.0.4057.1

このリリースでは、.NET Core 2.0 では、対象 sqlpackage のクロス プラットフォームのプレビュー ビルドを含むし、macOS、Linux で実行できます。 

このリリースでは、次の既知の問題の早期プレビュー版を示します。

- /P:CommandTimeout パラメーターは、120 に直接書き込まれます。
- ビルドと配置の共同作成者はサポートされていません。
  - System.ComponentModel.Composition.dll がサポートされている .NET Core 2.1 に移行した後で修正される予定です。
  - 大文字のパスを処理する必要があります。
- SQL Server の CLR UDT 型を含む、SQL CLR UDT 型はサポートされません。 SqlGeography、SqlGeometry、& SqlHierarchyId します。
- Json データのシリアル化を使用する古い .dacpac および .bacpac ファイルはサポートされていません。
- 参照先 .dacpacs (たとえば master.dacpac) 大文字小文字を区別するファイル システムに関する問題のため解決できません。
  - (たとえばマスター参照ファイルの名前を大文字に変換を回避するには。BACPAC)。
