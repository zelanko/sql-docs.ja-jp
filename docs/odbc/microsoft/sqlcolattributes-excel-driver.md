---
title: アトリビュート (Excel ドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], Excel Driver
ms.assetid: 7c4833e3-ff0c-4313-9ab8-21379ceab656
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 218c442af6292b665764ed60dc5586710d820de6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307943"
---
# <a name="sqlcolattributes-excel-driver"></a>SQLColAttributes (Excel ドライバー)
> [!NOTE]  
>  このトピックでは、Excel ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
|属性|説明|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|LONGVARBINARY データの場合、SQL_COLUMN_DISPLAY_SIZEは列の最大長であり、列の最大長は 2 です。|  
|SQL_OWNER_NAME|所有者名がサポートされていないため、この列には空の文字列 ("" ) が返されます。|  
|SQL_QUALIFIER_NAME|ディレクトリへのパスが返されます。|  
|SQL_COLUMN_SEARCHABLE|長い変数の列と長い変数の列はSQL_UNSEARCHABLEとして報告されます。<br /><br /> 長さ、可変長のバイナリー・データ・タイプおよび可変長データ・タイプは、LONGVARBINARY および LONGVARCHAR が検索可能でなくても検索可能です。|  
  
> [!NOTE]  
>  上記のリストは**SQLColAttributes**によって返される属性の完全なリストではありません。
