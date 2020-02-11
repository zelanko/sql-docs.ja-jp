---
title: ネイティブ コンパイル アドバイザー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
f1_keywords:
- sql12.swb.nativecompilationwizard.f1
- swb.nativecompilationwizard.f1
ms.assetid: d3898a47-2985-4a08-bc70-fd8331a01b7b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5174b5c859fa76ceeccdb99b7a46f510fd62d923
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63072771"
---
# <a name="native-compilation-advisor"></a>ネイティブ コンパイル アドバイザー
  トランザクションパフォーマンスレポートツール (「[テーブルまたはストアドプロシージャをインメモリ OLTP に移植する必要](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)があるかどうかを判断する」を参照) は、ネイティブコンパイルを使用するように移植した場合にメリットが得られる、データベース内の解釈されたストアドプロシージャについて通知します。 ネイティブ コンパイルを使用するように移植するストアド プロシージャを特定した後に、ネイティブ コンパイル アドバイザーを使用すると、解釈されたストアド プロシージャをネイティブ コンパイルに移行する際に役立ちます。 ネイティブ コンパイル ストアド プロシージャの詳細については、「 [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md)」をご覧ください。  
  
 まず、解釈されたストアド プロシージャが格納されているインスタンスに接続します。 
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] のインスタンスに接続できます。 ただし、アドバイザーを使用して移行操作を実行する場合は、インメモリ OLTP 機能が有効になっている [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] インスタンスに接続する必要があります。 インメモリ OLTP の要件の詳細については、「 [Requirements for Using Memory-Optimized Tables](memory-optimized-tables.md)」を参照してください。  
  
 移行方法については、「[In-Memory OLTP - Common Workload Patterns and Migration Considerations](https://msdn.microsoft.com/library/dn673538.aspx)」(インメモリ OLTP - 一般的なワークロード パターンと移行に関する考慮事項) を参照してください。  
  
## <a name="walkthrough-using-the-native-compilation-advisor"></a>ネイティブ コンパイル アドバイザーの使用に関するチュートリアル  
 
  **オブジェクト エクスプローラー**で、変換するストアド プロシージャを右クリックし、 **[ネイティブ コンパイル アドバイザー]** をクリックします。 これにより、 **[ストアド プロシージャのネイティブ コンパイル アドバイザー]** のようこそページが表示されます。 
  **[次へ]** をクリックして、続行します。  
  
### <a name="stored-procedure-validation"></a>[ストアド プロシージャの検証]  
 このページでは、ストアド プロシージャでネイティブ コンパイルと互換性のない構造が使用されているかどうかがレポートされます。 
  **[次へ]** をクリックすると、詳細を表示できます。 ネイティブ コンパイルと互換性のない構造がある場合は、 **[次へ]** をクリックすると、詳細を表示できます。  
  
### <a name="stored-procedure-validation-result"></a>[ストアド プロシージャの検証結果]  
 ネイティブ コンパイルと互換性のない構造がある場合は、 **[ストアド プロシージャの検証結果]** ページに詳細が表示されます。 レポートを生成 ( **[レポートの生成]** をクリック) し、 **ネイティブ コンパイル アドバイザー**を終了して、ネイティブ コンパイルと互換性があるようにコードを更新できます。  
  
## <a name="code-sample"></a>サンプル コード  
 次のサンプルは、解釈されたストアド プロシージャと、ネイティブ コンパイルに対する同等のストアド プロシージャを示しています。 次のサンプルでは、c:\data というディレクトリがあることを前提にしています。  
  
```sql  
CREATE DATABASE Demo  
ON  
PRIMARY(NAME = [Demo_data],  
FILENAME = 'C:\DATA\Demo_data.mdf', size=500MB)  
, FILEGROUP [Demo_fg] CONTAINS MEMORY_OPTIMIZED_DATA(  
NAME = [Demo_dir],  
FILENAME = 'C:\DATA\Demo_dir')  
LOG ON (name = [Demo_log], Filename='C:\DATA\Demo_log.ldf', size=500MB)  
COLLATE Latin1_General_100_BIN2;  
GO  
USE Demo;  
GO  
  
CREATE TABLE [dbo].[SalesOrders]  
(  
     [order_id] [int] NOT NULL,  
     [order_date] [datetime] NOT NULL,  
     [order_status] [tinyint] NOT NULL  
  
CONSTRAINT [PK_SalesOrders] PRIMARY KEY NONCLUSTERED HASH   
(  
     [order_id]  
)WITH ( BUCKET_COUNT = 2097152)  
)WITH ( MEMORY_OPTIMIZED = ON )  
  
go  
  
CREATE PROCEDURE [dbo].[InsertOrder] @id INT, @date DATETIME2, @status TINYINT  
AS   
BEGIN   
  
  INSERT dbo.SalesOrders VALUES (@id, @date, @status)  
  
END  
  
go  
  
CREATE PROCEDURE [dbo].[InsertOrderXTP] @id INT, @date DATETIME2, @status TINYINT  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS   
BEGIN ATOMIC WITH   
(    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
     LANGUAGE = N'us_english')  
  
  INSERT dbo.SalesOrders VALUES (@id, @date, @status)  
  
END  
go  
  
select * from SalesOrders  
go  
exec dbo.InsertOrder @id= 10, @date = '1956-01-01 12:00:00', @status = 1 ;  
exec dbo.InsertOrderXTP @id= 11, @date = '1956-01-01 12:01:00', @status = 2 ;  
select * from SalesOrders  
```  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP への移行](migrating-to-in-memory-oltp.md)  
  
  
