---
title: をクリックします。マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLGetTypeInfo
ms.assetid: 6e9ce02b-97c7-4c1a-91e0-829df7459c84
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 711652e22318d089b02fe8e79cb592f0a42dfff9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295132"
---
# <a name="sqlgettypeinfo-dbase-driver"></a>SQLGetTypeInfo (dBASE ドライバー)
> [!NOTE]  
>  このトピックでは、dBASE ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 **SQLGetTypeInfo**によって生成されるテーブルで返される型 (TYPE_NAME) の名前は、データ ソースで最も一般的に使用される名前になります。  
  
 SQL_ALL_EXCEPT_LIKEは、バイト、カウンター、倍精度、単精度、長整数型、および短いデータ型の SEARCHABLE 列に返されます。 (LIKE 機能は、ODBC 正規変換関数を使用して値を文字に変換し、比較を実行することによって実現できます。
