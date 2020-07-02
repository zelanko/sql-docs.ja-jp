---
title: Text 列と Image 列の管理 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- data types [ODBC], mapping
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 7b543556-ff36-4d35-ac08-de96223d92cd
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7a73a4417b16567622c60ab072d2c3cbf8134b69
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785590"
---
# <a name="managing-text-and-image-columns"></a>text 列と image 列の管理
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**text**、 **ntext**、および**image**データ (長いデータとも呼ばれます) は、 **char**、 **varchar**、 **binary**、または**varbinary**型の列に格納するデータ値が大きすぎる可能性がある文字またはバイナリ文字列データ型です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Text**データ型は、ODBC の SQL_LONGVARCHAR データ型にマップされます。**ntext**は SQL_WLONGVARCHAR にマップされるおよび**イメージ**は SQL_LONGVARBINARY にマップされます。 長いドキュメントや大きなビットマップなど、データ アイテムの中には大きすぎて適切にメモリに読み込むことができないものもあります。 シーケンシャルな部分から長いデータを取得するために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client ODBC ドライバーを使用すると、アプリケーションは[SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md)を呼び出すことができます。 長いデータをシーケンシャルな部分に送信するために、アプリケーションは[Sqlputdata](../../relational-databases/native-client-odbc-api/sqlputdata.md)を呼び出すことができます。 実行時にデータ送信に使われるパラメーターを、実行時データ パラメーターと呼びます。  
  
 アプリケーションでは、 **Sqlputdata**または**SQLGetData**を使用して (長いデータだけでなく) 任意の種類のデータを実際に書き込んだり、取得したりできます。ただし、部分では、**文字**と**バイナリ**データだけを送信または取得できます。 ただし、データが1つのバッファーに収まらない場合は、通常、 **Sqlputdata**または**SQLGetData**を使用する必要はありません。 バッファーをパラメーターまたは列にバインドする方がはるかに簡単です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [バインドされた text、image 型の列とバインドされない text、image 型の列](../../relational-databases/native-client-odbc-text-image-columns/bound-vs-unbound-text-and-image-columns.md)  
  
-   [ログに記録される変更と記録されない変更](../../relational-databases/native-client-odbc-text-image-columns/logged-vs-unlogged-modifications.md)  
  
-   [実行時データと Text 型、ntext 型、または Image 型の列](../../relational-databases/native-client-odbc-text-image-columns/data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>関連項目  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
