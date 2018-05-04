---
title: SQLGetTypeInfo (Paradox ドライバー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLGetTypeInfo
ms.assetid: e65063c7-ba9e-4cf0-ac13-4bb5bd2937db
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 300bc6086246abe0e6faff7801d12b4536520520
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgettypeinfo-paradox-driver"></a>SQLGetTypeInfo (Paradox ドライバー)
> [!NOTE]  
>  このトピックでは、Paradox ドライバー固有の情報を提供します。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 によって生成されるテーブルの型 (TYPE_NAME) の名前が返される**SQLGetTypeInfo**データ ソースによって最もよく使用される名前になります。  
  
 SQL_ALL_EXCEPT_LIKE が返されます、検索可能な列で、バイトのカウンター、Double、1 つの時間の長いと短い形式のデータ型。 (値を ODBC 標準の変換関数を使用する文字に変換することにより、LIKE の機能を実現できますと比較を実行します)。
