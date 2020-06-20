---
title: Text 列と Image 列の管理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: rothja
ms.author: jroth
ms.openlocfilehash: e9d7d5b0f48c68e8ac911f5e274c9afdb8cfe17d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85049699"
---
# <a name="managing-text-and-image-columns"></a>text 列と image 列の管理
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**text**、 **ntext**、および**image**データ (長いデータとも呼ばれます) は、 **char**、 **varchar**、 **binary**、または**varbinary**型の列に格納するデータ値が大きすぎる可能性がある文字またはバイナリ文字列データ型です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Text**データ型は、ODBC の SQL_LONGVARCHAR データ型にマップされます。**ntext**は SQL_WLONGVARCHAR にマップされるおよび**イメージ**は SQL_LONGVARBINARY にマップされます。 長いドキュメントや大きなビットマップなど、データ アイテムの中には大きすぎて適切にメモリに読み込むことができないものもあります。 シーケンシャルな部分から長いデータを取得するために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client ODBC ドライバーを使用すると、アプリケーションは[SQLGetData](../native-client-odbc-api/sqlgetdata.md)を呼び出すことができます。 長いデータをシーケンシャルな部分に送信するために、アプリケーションは[Sqlputdata](../native-client-odbc-api/sqlputdata.md)を呼び出すことができます。 実行時にデータ送信に使われるパラメーターを、実行時データ パラメーターと呼びます。  
  
 アプリケーションでは、 **Sqlputdata**または**SQLGetData**を使用して (長いデータだけでなく) 任意の種類のデータを実際に書き込んだり、取得したりできます。ただし、部分では、**文字**と**バイナリ**データだけを送信または取得できます。 ただし、データが1つのバッファーに収まらない場合は、通常、 **Sqlputdata**または**SQLGetData**を使用する必要はありません。 バッファーをパラメーターまたは列にバインドする方がはるかに簡単です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [バインドされた text、image 型の列とバインドされない text、image 型の列](bound-vs-unbound-text-and-image-columns.md)  
  
-   [ログに記録される変更と記録されない変更](logged-vs-unlogged-modifications.md)  
  
-   [実行時データと Text 型、ntext 型、または Image 型の列](data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
