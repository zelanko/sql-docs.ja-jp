---
title: データ ソースのデータの更新
description: データベース内のデータを変更するコマンドまたはストアド プロシージャを実行する方法について説明します。
ms.date: 11/25/2020
dev_langs:
- csharp
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 41b81d0adedf48f0e33efe6c60d83dd4ed7b597a
ms.sourcegitcommit: debaff72dbfae91b303f0acd42dd6d99e03135a2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96428247"
---
# <a name="updating-data-in-a-data-source"></a>データ ソースのデータの更新

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

データを変更する SQL ステートメント (INSERT、UPDATE、DELETE など) は行を返しません。 同様に、多くのストアド プロシージャは、アクションを実行しても行を返しません。 行を返さないコマンドを実行するには、適切な SQL コマンドを使用して **Command** オブジェクトを作成し、必要な **Parameters** を含む **Connection** を作成します。 <xref:Microsoft.Data.SqlClient.SqlCommand> オブジェクトの <xref:Microsoft.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> メソッドでコマンドを実行します。

> [!NOTE]
> **ExecuteNonQuery** メソッドからは、実行されたステートメントまたはストアド プロシージャの影響を受けた行数を表す整数が返されます。 複数のステートメントが実行された場合は、実行された各ステートメントの影響を受けたレコードの合計を示す値が返されます。

## <a name="example"></a>例

INSERT ステートメントを実行して、**ExecuteNonQuery** でデータベースにレコードを挿入するコードの例を次に示します。
  
[!code-csharp[DataWorks SqlCommand.ExecuteNonQuery#1](~/../sqlclient/doc/samples/SqlCommand_ExecuteNonQuery_SP_DML.cs#1)]

「[カタログ操作の実行](perform-catalog-operations.md)」と同じコードで作成されたストアド プロシージャを実行するコードの例を次に示します。 ストアド プロシージャは行を返さないため **ExecuteNonQuery** メソッドが使用されていますが、ストアド プロシージャは入力パラメーターを受け取り、出力パラメーターと戻り値を返します。

[!code-csharp[DataWorks SqlCommand.ExecuteNonQuery#2](~/../sqlclient/doc/samples/SqlCommand_ExecuteNonQuery_SP_DML.cs#2)]

## <a name="see-also"></a>関連項目

- [コマンドを使用したデータ変更](use-commands-to-modify-data.md)
- [コマンドとパラメーター](commands-parameters.md)
