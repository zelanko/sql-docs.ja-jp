---
title: SQLTables (アクセス ドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLTables function [ODBC], Access Driver
- Access driver [ODBC], SQLTables
ms.assetid: 94423cf9-341a-4db6-bb10-8f5448df7fc3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: df3a23af365efbef6a0f0da2c52568501425ecb3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306093"
---
# <a name="sqltables-access-driver"></a>SQLTables (Access ドライバー)
> [!NOTE]  
>  このトピックでは、アクセス ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
|引数|説明|  
|--------------|--------------|  
|*所有者*|*szTableOwner*の唯一の有効な引数は、どのドライバーも所有者名をサポートしていないため NULL です。 *szTableOwner が*NULL に設定されている場合、すべてのテーブルが返されます。 TABLE_OWNER列に NULL が返されます。|  
|*修飾子*|TABLE_QUALIFIER列では **、SQLTables**はデータベース ファイルへのパスを返します。|  
|*SZ テーブルタイプ*|Access ドライバを使用する場合、システム テーブルの*szTableType*に対して "SYSTEM TABLE" がサポートされ、アタッチ テーブルでは "SYNONYM" がサポートされ、行を返すクエリでは "VIEW" がサポートされます。|  
  
## <a name="see-also"></a>参照  
 [SQLTables 関数](../../odbc/reference/syntax/sqltables-function.md)
