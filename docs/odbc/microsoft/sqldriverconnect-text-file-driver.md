---
title: SQLDriverConnect (テキストファイルドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Text File Driver
- text file driver [ODBC], SQLDriverConnect
ms.assetid: d7769021-bd18-4d8e-96e0-e184a82d6ca3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f9343361e7ad6fbfdf68b82218a39a56fa8d928e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053912"
---
# <a name="sqldriverconnect-text-file-driver"></a>SQLDriverConnect (テキスト ファイル ドライバー)
> [!NOTE]  
>  このトピックでは、テキストファイルドライバー固有の情報について説明します。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 **SQLDriverConnect**を使用すると、データソース (DSN) を作成せずにドライバーに接続できます。  
  
 すべてのドライバーの接続文字列では、 **DSN**、 **dbq**、および**FIL**の各キーワードがサポートされています。  
  
 次の表は、各ドライバーに接続するために必要な最低限のキーワードと、 **SQLDriverConnect**で使用されるキーワードと値のペアの例を示しています。 DRIVERID 値の完全な一覧については、「 [Sqlconfigdatasource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)」を参照してください。  
  
> [!NOTE]  
>  テキストドライバーに DBQ または DefaultDir が指定されていない場合、ドライバーは現在のディレクトリに接続します。  
  
|Driver|キーワードが必要です|例|  
|------------|-----------------------|--------------|  
|Text|Driver|Driver = {Microsoft Text Driver (* .txt;\*.csv)};DefaultDir = c:\temp|
