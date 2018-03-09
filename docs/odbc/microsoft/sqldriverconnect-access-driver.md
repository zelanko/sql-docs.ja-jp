---
title: "SQLDriverConnect (Access ドライバー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Access driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], Access Driver
ms.assetid: 9d133e9b-7545-464d-aa3c-677fa7e2a41d
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7362786d12678d90554cb0e7dab2d612fd061d2b
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="sqldriverconnect-access-driver"></a>SQLDriverConnect (Access ドライバー)
> [!NOTE]  
>  このトピックでは、アクセス ドライバー固有の情報を提供します。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 **SQLDriverConnect**データ ソース (DSN) を作成せずに、ドライバーに接続することができます。  
  
 すべてのドライバーの接続文字列で、次のキーワードはサポートされて: **DSN**、 **DBQ**、および**FIL**です。  
  
 **UID**と**PWD**キーワードもサポートされています。  
  
 PWD キーワードを含めないでくださいの特殊文字 (で SQL_SPECIAL_CHARACTERS を参照してください**SQLGetInfo**返された値)。  
  
 次の表は、各ドライバーへの接続に必要な最小のキーワードを示しています、併用キーワード/値ペアの例を示します**SQLDriverConnect**です。 DRIVERID 値の一覧については、次を参照してください。 [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)です。  
  
|Driver|必要なキーワード|使用例|  
|------------|-----------------------|--------------|  
|Microsoft Access|ドライバー、DBQ|ドライバー {Microsoft Access ドライバー (*.mdb)} を = です。DBQ = c:\\\temp\\\sample.mdb|
