---
title: を取得する情報 (アクセス ドライバー) |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ddfa9bd29f0834adf1c211f9b8a111db0b94d3fe
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295152"
---
# <a name="sqlgettypeinfo-access-driver"></a>SQLGetTypeInfo (Access ドライバー)
> [!NOTE]  
>  このトピックでは、アクセス ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 **SQLGetTypeInfo**によって生成されるテーブルで返される型 (TYPE_NAME) の名前は、データ ソースで最も一般的に使用される名前になります。  
  
 SQL_ALL_EXCEPT_LIKEは、バイト、カウンター、倍精度、単精度、長整数型、および短いデータ型の SEARCHABLE 列に返されます。 (LIKE 機能は、ODBC 正規変換関数を使用して値を文字に変換し、比較を実行することによって実現できます。
