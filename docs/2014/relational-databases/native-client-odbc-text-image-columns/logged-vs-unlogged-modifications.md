---
title: ログ記録と Unlogged の変更 |Microsoft Docs
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
- data types [ODBC], image
- data types [ODBC], text
- logged vs. nonlogged modifications [SQL Server Native Client]
- columns [ODBC]
- ODBC data types, image columns
- nonlogged vs. logged modifications
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 20aa5b27-4a2c-46e7-8356-beb0eebf4b7e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c722d5360ad01e7e95508c2219ceb674de381286
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63195134"
---
# <a name="logged-vs-unlogged-modifications"></a>ログに記録される変更と記録されない変更
  アプリケーションで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、NATIVE Client ODBC ドライバーが**text**、 **ntext**、および**image**の変更をログに記録しないように要求できます。 ただし、このオプションの使用には注意が必要です。 **Text**型、 **ntext**型、または**image**型のデータが重要ではなく、データ所有者がデータを回復してパフォーマンスを向上させることができない場合にのみ使用してください。  
  
 **Text**、 **ntext**、および**image**の変更のログ記録は、*属性*パラメーターを SQL_SOPT_SS_ TEXTPTR_LOGGING に設定し、 *valueptr*を SQL_TL_ON または SQL_TL_OFF に設定して、 [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)を呼び出すことによって制御されます。  
  
## <a name="see-also"></a>参照  
 [text 列と image 列の管理](managing-text-and-image-columns.md)  
  
  
