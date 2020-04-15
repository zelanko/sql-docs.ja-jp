---
title: SQL テーブル (エクセル ドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLTables
- SQLTables function [ODBC], Excel Driver
ms.assetid: 9410b686-4b5b-4b51-b5ef-f9d2e7a48faa
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c436a1f52a862cda753d8c043515f5584607d98c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299302"
---
# <a name="sqltables-excel-driver"></a>SQLTables (Excel ドライバー)
> [!NOTE]  
>  このトピックでは、Excel ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
|引数|説明|  
|--------------|--------------|  
|*所有者*|*szTableOwner*の唯一の有効な引数は、どのドライバーも所有者名をサポートしていないため NULL です。 *szTableOwner が*NULL に設定されている場合、すべてのテーブルが返されます。 TABLE_OWNER列に NULL が返されます。|  
|*修飾子*|Microsoft Excel 3.0 または 4.0 ドライバーを使用する場合、既存のテーブルの名前ではない*szTableQualifier*の値を使用して**SQLTables**を呼び出すと、ドライバーは、その名前のテーブルを作成します。<br /><br /> TABLE_QUALIFIER列では **、SQLTables は**ディレクトリへのパスを返します。|  
|*SZ テーブルタイプ*|Excel 3.0 または 4.0 では、テーブルの種類が "TABLE" のみサポートされています。<br /><br /> Microsoft Excel ファイルの新しいバージョンでは、シート名 (末尾に "$" が付いたテーブル) に "SYSTEM TABLE" が返され、ワークシート内のテーブルに対して "TABLE" が返されます。|
