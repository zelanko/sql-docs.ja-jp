---
title: SQL カラム (パラドックス ドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColumns function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLColumns
ms.assetid: d7831c7d-8be9-40a7-bc70-8d89db8fe8c9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 66bc244089af548413046357aae6371ff0c39bbf
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307869"
---
# <a name="sqlcolumns-paradox-driver"></a>SQLColumns (Paradox ドライバー)
> [!NOTE]  
>  このトピックでは、Paradox ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
|列|説明|  
|------------|--------------|  
|TABLE_QUALIFIER|ディレクトリへのパスが返されます。|  
|TABLE_OWNER|所有者名がサポートされていないため、この列には NULL が戻されます。|  
|NULLABLE|SQL_NO_NULLSは、主キーまたは一意のインデックスに含まれる列に対して返されます。|
