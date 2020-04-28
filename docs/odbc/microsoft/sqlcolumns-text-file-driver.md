---
title: SQLColumns (テキストファイルドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLColumns
- SQLColumns function [ODBC], Text File Driver
ms.assetid: c99e5f8d-4e43-48f8-9e0e-086707b411f5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 78c2e20f12dedf399ab36dd908f83aa93bebffc4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307870"
---
# <a name="sqlcolumns-text-file-driver"></a>SQLColumns (テキスト ファイル ドライバー)
> [!NOTE]  
>  このトピックでは、テキストファイルドライバー固有の情報について説明します。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
|列|説明|  
|------------|--------------|  
|TABLE_QUALIFIER|ディレクトリへのパスが返されます。|  
|TABLE_OWNER|所有者名がサポートされていないため、この列には NULL が返されます。|  
|NULLABLE|主キーまたは一意のインデックスに含まれる列に対して SQL_NO_NULLS が返されます。|
