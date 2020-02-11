---
title: SQLDriverConnect (Access Driver) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], Access Driver
ms.assetid: 9d133e9b-7545-464d-aa3c-677fa7e2a41d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e211797147c4da8f197247244f6f2805185b3b0b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053983"
---
# <a name="sqldriverconnect-access-driver"></a>SQLDriverConnect (Access ドライバー)
> [!NOTE]  
>  このトピックでは、ドライバー固有の情報にアクセスします。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 **SQLDriverConnect**を使用すると、データソース (DSN) を作成せずにドライバーに接続できます。  
  
 すべてのドライバーの接続文字列では、 **DSN**、 **dbq**、および**FIL**の各キーワードがサポートされています。  
  
 **UID**キーワードと**PWD**キーワードもサポートされています。  
  
 PWD キーワードには、特殊文字を含めることはできません (「 **SQLGetInfo**が返す値の SQL_SPECIAL_CHARACTERS」を参照してください)。  
  
 次の表は、各ドライバーに接続するために必要な最低限のキーワードと、 **SQLDriverConnect**で使用されるキーワードと値のペアの例を示しています。 DRIVERID 値の完全な一覧については、「 [Sqlconfigdatasource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)」を参照してください。  
  
|Driver|キーワードが必要です|例|  
|------------|-----------------------|--------------|  
|Microsoft Access|ドライバー、DBQ|Driver = {Microsoft Access Driver (* .mdb)};DBQ = c:\\\temp\\、mdb|
