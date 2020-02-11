---
title: SQLColumns (Access Driver) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColumns function [ODBC], Access Driver
- Access driver [ODBC], SQLColumns
ms.assetid: 1eac255c-6110-4805-a1bc-feee1eec35d0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2916532b9dd79e25adce791b2201d77eb2cdff84
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67985253"
---
# <a name="sqlcolumns-access-driver"></a>SQLColumns (Access ドライバー)
> [!NOTE]  
>  このトピックでは、ドライバー固有の情報にアクセスします。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
|列|説明|  
|------------|--------------|  
|TABLE_QUALIFIER|データベースファイルへのパスが返されます。|  
|TABLE_OWNER|所有者名がサポートされていないため、この列には NULL が返されます。|  
|NULLABLE|主キーまたは一意のインデックスに含まれる列に対して SQL_NO_NULLS が返されます。|
