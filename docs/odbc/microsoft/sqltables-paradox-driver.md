---
title: SQLTables (パラドックスドライバ) |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: aa13b5395d8f3c2cb470a4eff1b1ef02a43bad53
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299290"
---
# <a name="sqltables-paradox-driver"></a>SQLTables (Paradox ドライバー)
> [!NOTE]  
>  このトピックでは、Paradox ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
|引数|説明|  
|--------------|--------------|  
|*所有者*|*szTableOwner*の唯一の有効な引数は、どのドライバーも所有者名をサポートしていないため NULL です。 *szTableOwner が*NULL に設定されている場合、すべてのテーブルが返されます。 TABLE_OWNER列に NULL が返されます。|  
|*修飾子*|TABLE_QUALIFIER列では **、SQLTables は**ディレクトリへのパスを返します。|  
|*SZ テーブルタイプ*|Paradox ファイルの場合、"TABLE" だけがサポートされるテーブルの種類です。|  
  
## <a name="see-also"></a>参照  
 [SQLTables 関数](../../odbc/reference/syntax/sqltables-function.md)
