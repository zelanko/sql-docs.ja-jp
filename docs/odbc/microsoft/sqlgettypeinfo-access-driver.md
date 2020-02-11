---
title: SQLGetTypeInfo (Access Driver) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLGetTypeInfo
- SQLGetTypeInfo function [ODBC], Access Driver
ms.assetid: a28b16eb-ca36-4297-9297-ecd7c107a84e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 788f0b8c69636ad9bf93de73632abc911a0fb0e3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67898759"
---
# <a name="sqlgettypeinfo-access-driver"></a>SQLGetTypeInfo (Access ドライバー)
> [!NOTE]  
>  このトピックでは、ドライバー固有の情報にアクセスします。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 **SQLGetTypeInfo**によって生成されるテーブルに返される型の名前 (TYPE_NAME) は、データソースで最もよく使用される名前になります。  
  
 SQL_ALL_EXCEPT_LIKE は、Byte、Counter、Double、Single、Long、Short の各データ型の検索可能な列に返されます。 (LIKE 機能は、ODBC 正規変換関数を使用して値を文字に変換してから、比較を実行することで実現できます)。
