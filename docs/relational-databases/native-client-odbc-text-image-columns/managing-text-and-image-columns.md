---
title: "テキストとイメージの列を管理する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-text-image-columns
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
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
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3efc4cf8660055e007d55bb16c7002632b33bdbf
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="managing-text-and-image-columns"></a>text 列と image 列の管理
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**テキスト**、 **ntext**、および**イメージ**データ (長い形式のデータとも呼ばれる) は文字またはバイナリ文字列データ型に収まらないほど大きなデータ値を保持できる**char**、 **varchar**、**バイナリ**、または**varbinary**列です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **テキスト**データ型、ODBC SQL_LONGVARCHAR データ型にマップ**ntext** SQL_WLONGVARCHAR; にマップし、**イメージ**SQL_LONGVARBINARY にマップします。 長いドキュメントや大きなビットマップなど、データ アイテムの中には大きすぎて適切にメモリに読み込むことができないものもあります。 長いデータの取得先[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、シーケンシャルな部分に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーにより、アプリケーションを呼び出す[SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md)です。 連続したブロックで長い形式のデータを送信するアプリケーションを呼び出すことができます[SQLPutData](../../relational-databases/native-client-odbc-api/sqlputdata.md)です。 実行時にデータ送信に使われるパラメーターを、実行時データ パラメーターと呼びます。  
  
 アプリケーションが実際に作成またはであらゆる種類のデータ (データの長さだけがありません) を取得**SQLPutData**または**SQLGetData**にのみ、**文字**と**バイナリ**データを送信または部分で取得することができます。 ただし、データがそれほど 1 つのバッファーに収まらない場合は通常を使用する理由**SQLPutData**または**SQLGetData**です。 バッファーをパラメーターまたは列にバインドする方がはるかに簡単です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [バインドされた text、image 型の列とバインドされない text、image 型の列](../../relational-databases/native-client-odbc-text-image-columns/bound-vs-unbound-text-and-image-columns.md)  
  
-   [ログに記録される変更と記録されない変更](../../relational-databases/native-client-odbc-text-image-columns/logged-vs-unlogged-modifications.md)  
  
-   [実行時データと Text 型、ntext 型、または Image 型の列](../../relational-databases/native-client-odbc-text-image-columns/data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
