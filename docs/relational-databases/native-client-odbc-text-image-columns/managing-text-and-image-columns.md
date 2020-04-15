---
title: テキスト列と画像列の管理 |マイクロソフトドキュメント
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
ms.openlocfilehash: d3ac58e59f66dd107a9523a42f5647c90b4fb737
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297719"
---
# <a name="managing-text-and-image-columns"></a>text 列と image 列の管理
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**text**、 **ntext**、および**image**データ (long データとも呼ばれる) は、文字型またはバイナリ文字列データ型で、**文字** **、varchar**、**バイナリ**、または**varbinary**の各列に収まるには大きすぎるデータ値を保持できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**テキスト**データ型は ODBC SQL_LONGVARCHAR データ型にマップされます。**ntext**はSQL_WLONGVARCHARにマップされます。SQL_LONGVARBINARYに**画像**マップを作成します。 長いドキュメントや大きなビットマップなど、データ アイテムの中には大きすぎて適切にメモリに読み込むことができないものもあります。 ネイティブ クライアント ODBC[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ドライバーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]連続した部分から長いデータを取得する、アプリケーションは[SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md)を呼び出します。 長いデータを順次に送信するために、アプリケーションは[SQLPutData](../../relational-databases/native-client-odbc-api/sqlputdata.md)を呼び出すことができます。 実行時にデータ送信に使われるパラメーターを、実行時データ パラメーターと呼びます。  
  
 アプリケーションは **、SQLPutData**または**SQLGetData**を使用して、実際には任意の種類のデータ (長いデータだけでなく) を書き込みまたは取得できますが、**文字**データと**バイナリ**データのみを部分的に送信または取得できます。 ただし、データが 1 つのバッファーに収まるほど小さい場合は、通常 **、SQLPutData**または**SQLGetData**を使用する理由はありません。 バッファーをパラメーターまたは列にバインドする方がはるかに簡単です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [バインドされた text、image 型の列とバインドされない text、image 型の列](../../relational-databases/native-client-odbc-text-image-columns/bound-vs-unbound-text-and-image-columns.md)  
  
-   [ログに記録される変更と記録されない変更](../../relational-databases/native-client-odbc-text-image-columns/logged-vs-unlogged-modifications.md)  
  
-   [実行時データと Text 型、ntext 型、または Image 型の列](../../relational-databases/native-client-odbc-text-image-columns/data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
