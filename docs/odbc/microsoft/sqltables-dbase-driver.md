---
title: SQLTables (dBASE ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBase driver [ODBC], SQLTables
- SQLTables function [ODBC], dBASE Driver
ms.assetid: 45938efb-b678-47d8-9345-644fa26ad679
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 63e42091ed0e1763cb24eef5e6a32f551b29ad5f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62686779"
---
# <a name="sqltables-dbase-driver"></a>SQLTables (dBASE ドライバー)
> [!NOTE]  
>  このトピックでは、dBASE ドライバー固有の情報を提供します。 この関数の詳細については、該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)します。  
  
|引数|コメント|  
|--------------|--------------|  
|*szTableOwner*|唯一の有効な引数*szTableOwner* NULL は、所有者名、ドライバーのいずれもサポートしているためです。 *SzTableOwner*を NULL に設定すると、すべてのテーブルが返されます。 TABLE_OWNER 列で NULL が返されます。|  
|*szTableQualifier*|TABLE_QUALIFIER 列で、 **SQLTables**ディレクトリへのパスを返します。|  
|*SzTableType*|DBASE ファイルでは、"TABLE"はサポートされている唯一のテーブル型です。|
