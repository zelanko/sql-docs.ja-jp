---
title: SQLTables (Paradox ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Paradox driver [ODBC], SQLTables
- SQLTables function [ODBC], Paradox Driver
ms.assetid: d68adad6-97bd-4b47-bcf9-0102aafb00d4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 48cbc19506a7f695433489c952f53864b614a05e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67949024"
---
# <a name="sqltables-paradox-driver"></a>SQLTables (Paradox ドライバー)
> [!NOTE]  
>  このトピックでは、Paradox ドライバー固有の情報について説明します。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
|引数|説明|  
|--------------|--------------|  
|*szTableOwner*|すべてのドライバーで所有者名がサポートされていないため、 *Sztableowner*の有効な引数は NULL だけです。 *Sztableowner*を NULL に設定すると、すべてのテーブルが返されます。 TABLE_OWNER 列に NULL が返されます。|  
|*szTableQualifier*|TABLE_QUALIFIER 列では、 **Sqltables**はディレクトリへのパスを返します。|  
|*SzTableType*|Paradox ファイルの場合、サポートされているテーブル型は "TABLE" だけです。|  
  
## <a name="see-also"></a>参照  
 [SQLTables 関数](../../odbc/reference/syntax/sqltables-function.md)
