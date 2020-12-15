---
title: DataReader によってデータを取得する
description: ADO.NET で DataReader を使用してデータを取得する方法について、サンプル コードで説明します。 DataReader は、バッファリングされないデータ ストリームを提供します。
ms.date: 11/30/2020
dev_langs:
- csharp
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 06bfaa994c2b29959f44cfc554122465db9e0394
ms.sourcegitcommit: c127c0752e84cccd38a7e23ac74c0362a40f952e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2020
ms.locfileid: "96772226"
---
# <a name="retrieve-data-by-a-datareader"></a>DataReader によってデータを取得する

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

**DataReader** を使用してデータを取得するには、**Command** オブジェクトのインスタンスを作成した後、**Command.ExecuteReader** を呼び出して **DataReader** を作成し、データ ソースから行を取得します。 **DataReader** では、手続きロジックがデータ ソースからの結果を順番に効率的に処理できるようにするバッファリングされないデータ ストリームが提供されます。

> [!NOTE]
> **DataReader** はデータをメモリにキャッシュしないため、大量のデータを取得する場合に適しています。

**DataReader** を使用する例を次に示します。ここで、`reader` は有効な DataReader を、`command` は有効な Command オブジェクトを表します。  

```csharp
reader = command.ExecuteReader();  
```

クエリ結果から行を取得するには、**DataReader.Read** メソッドを使用します。 返された行の各列にアクセスするには、その列の名前または序数を **DataReader** に渡します。 ただし、**DataReader** では、最適のパフォーマンスが得られるように、ネイティブのデータ型を使用して列の値にアクセスできる一連のメソッド (**GetDateTime**、**GetDouble**、**GetGuid**、**GetInt32** など) が提供されています。 データ プロバイダー固有の **DataReaders** の型指定されたアクセサー メソッドの一覧については、「<xref:Microsoft.Data.SqlClient.SqlDataReader>」を参照してください。 基になるデータ型がわかっているときは、型指定されたアクセサー メソッドを使用すると、列の値を取得するときに必要な型変換の量が少なくなります。  

次に、**DataReader** オブジェクトを反復処理して各行から 2 つの列を返す例を示します。  

[!code-csharp[DataWorks SqlClient.HasRows#1](~/../sqlclient/doc/samples/SqlDataReader_HasRows.cs#1)]

## <a name="closing-the-datareader"></a>DataReader の終了  

**DataReader** オブジェクトを使い終えたら、**Close** メソッドを必ず呼び出します。

> [!NOTE]
> **Command** に出力パラメーターまたは戻り値が含まれている場合、**DataReader** が閉じられるまで、それらの値を使用することはできません。  

> [!IMPORTANT]
> **DataReader** が開かれている間、**Connection** はその **DataReader** によって排他的に使用されています。 元の **DataReader** が閉じられるまでは、別の **DataReader** の作成など、どのようなコマンドもその **Connection** に対して実行できません。  

> [!NOTE]
> クラスの **Finalize** メソッド内では、**Connection**、**DataReader**、またはその他のマネージド オブジェクトに対して、**Close** または **Dispose** を呼び出さないでください。 終了処理では、クラスに直接所有されているアンマネージ リソースだけを解放してください。 クラスがアンマネージド リソースを所有していない場合は、クラス定義に **Finalize** メソッドを含めないでください。 詳しくは、「[ガベージ コレクション](/dotnet/standard/garbage-collection/index.md)」をご覧ください。
 
## <a name="retrieve-multiple-result-sets-using-nextresult"></a>NextResult による複数の結果セットの取得

**DataReader** から複数の結果セットが返される場合は、**NextResult** メソッドを呼び出して、結果セットを順番に反復処理します。 <xref:Microsoft.Data.SqlClient.SqlDataReader> メソッドを使用して、2 つの SELECT ステートメントの結果を処理する <xref:Microsoft.Data.SqlClient.SqlCommand.ExecuteReader%2A> の例を次に示します。  

[!code-csharp[DataWorks SqlClient.NextResult#1](~/../sqlclient/doc/samples/SqlDataReader_NextResult.cs#1)]

## <a name="get-schema-information-from-the-datareader"></a>DataReader からのスキーマ情報の取得  

**DataReader** が開かれている間に **GetSchemaTable** メソッドを使用して、現在の結果セットについてのスキーマ情報を取得できます。 **GetSchemaTable** は、現在の結果セットのスキーマ情報を含む行と列が設定されている <xref:System.Data.DataTable> オブジェクトを返します。 **DataTable** には結果セットの列ごとに 1 行が設定されます。 スキーマ テーブルの各列は、結果セットの行で返される列の 1 つのプロパティにマップされます。**ColumnName** はそのプロパティの名前であり、列の値はプロパティの値です。 **DataReader** のスキーマ情報を出力する例を次に示します。  

[!code-csharp[DataWorks SqlClient.GetSchemaTable#1](~/../sqlclient/doc/samples/SqlDataReader_GetSchemaTable.cs#1)]

## <a name="see-also"></a>関連項目

- [DataAdapter と DataReader](dataadapters-datareaders.md)
- [コマンドとパラメーター](commands-parameters.md)
- [Microsoft ADO.NET for SQL Server](microsoft-ado-net-sql-server.md)
