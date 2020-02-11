---
title: SQLDriverConnect (Paradox ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLDriverConnect
ms.assetid: c2ba486e-5e01-4e67-adb1-68511f5f0206
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e17ca12e0c8745dcad30a3e5ce2c9689b041e7d2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67967483"
---
# <a name="sqldriverconnect-paradox-driver"></a>SQLDriverConnect (Paradox ドライバー)
> [!NOTE]  
>  このトピックでは、Paradox ドライバー固有の情報について説明します。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 **SQLDriverConnect**を使用すると、データソース (DSN) を作成せずにドライバーに接続できます。  
  
 すべてのドライバーの接続文字列では、 **DSN**、 **dbq**、および**FIL**の各キーワードがサポートされています。  
  
 **PWD**キーワードもサポートされています。 PWD キーワードには、特殊文字を含めることはできません (「 **SQLGetInfo**が返す値の SQL_SPECIAL_CHARACTERS」を参照してください)。  
  
 パスワードで保護されたファイルをユーザーが開いた後、他のユーザーは同じファイルを開くことができません。  
  
 次の表は、各ドライバーに接続するために必要な最低限のキーワードと、 **SQLDriverConnect**で使用されるキーワードと値のペアの例を示しています。 DRIVERID 値の完全な一覧については、「 [Sqlconfigdatasource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)」を参照してください。  
  
> [!NOTE]  
>  Paradox ドライバーに DBQ または DefaultDir が指定されていない場合、ドライバーは現在のディレクトリに接続します。  
  
|Driver|キーワードが必要です|例|  
|------------|-----------------------|-------------|  
|Paradox|ドライバー、DriverID|Driver = {Microsoft Paradox Driver (* db)};DBQ = c:\temp; DriverID = 26|
