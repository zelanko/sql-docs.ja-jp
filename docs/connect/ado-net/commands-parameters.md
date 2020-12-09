---
title: コマンドおよびパラメーター
description: Microsoft SqlClient Data Provider for SQL Server 用の Command オブジェクトを使用してコマンドを実行し、データ ソースから結果を返す方法について説明します。
ms.date: 11/25/2020
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 931c36619f5eaed0159ee04db3a08eb745634698
ms.sourcegitcommit: debaff72dbfae91b303f0acd42dd6d99e03135a2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96428279"
---
# <a name="commands-and-parameters"></a>コマンドおよびパラメーター

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

データ ソースへの接続を確立した後、<xref:System.Data.Common.DbCommand> オブジェクトを使用してコマンドを実行し、データ ソースから結果を返すことができます。 Microsoft SqlClient Data Provider for SQL Server 用のコマンド コンストラクターのいずれかを使用して、コマンドを作成できます。 コンストラクターには、データ ソースで実行する SQL ステートメント、<xref:System.Data.Common.DbConnection> オブジェクト、<xref:System.Data.Common.DbTransaction> オブジェクトなど、オプションの引数を渡すことができます。

これらのオブジェクトをコマンドのプロパティとして構成することもできます。 また、<xref:System.Data.Common.DbConnection.CreateCommand%2A> オブジェクトの `DbConnection` メソッドを使用して、特定の接続用のコマンドを作成することもできます。 コマンドによって実行される SQL ステートメントは、<xref:System.Data.Common.DbCommand.CommandText%2A> プロパティを使って構成できます。 Microsoft SqlClient Data Provider for SQL Server には、<xref:Microsoft.Data.SqlClient.SqlCommand> オブジェクトがあります。

## <a name="in-this-section"></a>このセクションの内容

[コマンドの実行](execute-command.md) ADO.NET `Command` オブジェクトについて、またそれを使用してデータ ソースに対してクエリとコマンドを実行する方法について説明します。

[パラメーターの構成](configure-parameters.md) `Command` パラメーターの使用方法について説明します。たとえば方向、データ型、パラメーター構文などです。

[CommandBuilder を使用したコマンドの生成](generate-commands-with-commandbuilders.md)  
`DataAdapter` に単一テーブルを対象とする SELECT コマンドが割り当てられているときに、コマンド ビルダーを使用して INSERT、UPDATE、DELETE の各コマンドを自動的に生成する方法について説明します。

[データベースからの単一の値の取得](obtain-single-value-from-database.md) `Command` オブジェクトの `ExecuteScalar` メソッドを使用して、データベース クエリから単一の値を返す方法について説明します。

[コマンドを使用したデータ変更](use-commands-to-modify-data.md) Microsoft SqlClient Data Provider for SQL Server を使用して、ストアド プロシージャやデータ定義言語 (DDL) ステートメントを実行する方法について説明します。

## <a name="see-also"></a>関連項目

- [データ ソースへの接続](connecting-to-data-source.md)
