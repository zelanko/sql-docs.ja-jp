---
title: SQL テーブル (dBASE ドライバー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBase driver [ODBC], SQLTables
- SQLTables function [ODBC], dBASE Driver
ms.assetid: 45938efb-b678-47d8-9345-644fa26ad679
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 242be06eafc7657f37f55ce266af471cbc72597f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306073"
---
# <a name="sqltables-dbase-driver"></a>SQLTables (dBASE ドライバー)
> [!NOTE]  
>  このトピックでは、dBASE ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
|引数|説明|  
|--------------|--------------|  
|*所有者*|どのドライバーも所有者名をサポートしていないため *、szTableOwner*の唯一の有効な引数は NULL です。 *szTableOwner が*NULL に設定されている場合、すべてのテーブルが返されます。 TABLE_OWNER列に NULL が返されます。|  
|*修飾子*|TABLE_QUALIFIER列では **、SQLTables は**ディレクトリへのパスを返します。|  
|*SZ テーブルタイプ*|dBASE ファイルの場合、"TABLE" だけがサポートされるテーブルタイプです。|
