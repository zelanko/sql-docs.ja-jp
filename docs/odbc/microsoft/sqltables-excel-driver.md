---
title: "SQLTables (Excel ドライバー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Excel driver [ODBC], SQLTables
- SQLTables function [ODBC], Excel Driver
ms.assetid: 9410b686-4b5b-4b51-b5ef-f9d2e7a48faa
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 68c0c6f2ad3e4cac7eb6f708998777c17bea5a7c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqltables-excel-driver"></a>SQLTables (Excel ドライバー)
> [!NOTE]  
>  このトピックでは、Excel ドライバーに固有の情報を提供します。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
|引数|コメント|  
|--------------|--------------|  
|*szTableOwner*|唯一の有効な引数*szTableOwner* NULL では、ドライバーのサポート所有者名。 *SzTableOwner*を NULL に設定すると、すべてのテーブルが返されます。 TABLE_OWNER 列に NULL が返されます。|  
|*szTableQualifier*|Microsoft Excel 3.0 または 4.0 のドライバーを使用する場合、呼び出す場合は、 **SQLTables**に値を持つ*szTableQualifier*外にある既存のテーブルの名前、ドライバーはその名前を持つテーブルを作成します。<br /><br /> TABLE_QUALIFIER 列で**SQLTables**ディレクトリへのパスを取得します。|  
|*SzTableType*|Microsoft Excel 3.0 または 4.0 では、"TABLE"はサポートされている唯一のテーブル型です。<br /><br /> 以降のバージョンの Microsoft Excel ファイルでは、シートの名前 (末尾に「$」でテーブル) の「システム テーブル」が返されます、ワークシート内のテーブルの"TABLE"が返されます。|
