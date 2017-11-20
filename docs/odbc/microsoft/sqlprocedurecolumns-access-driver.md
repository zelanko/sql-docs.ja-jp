---
title: "SQLProcedureColumns (Access ドライバー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Access driver [ODBC], SQLProcedureColumns
- SQLProcedureColumns function [ODBC], Access Driver
ms.assetid: 34fee995-5848-4ecb-bda0-fc362a77b2d9
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9faec06a2337e7b3a2e93769486f40e006d9d7c8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlprocedurecolumns-access-driver"></a>SQLProcedureColumns (Access ドライバー)
> [!NOTE]  
>  このトピックでは、アクセス ドライバー固有の情報を提供します。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 アプリケーション開発者は、結果セットの末尾から開始し、逆方向に進みますドライバーで定義された列を探してください。  
  
|列|コメント|  
|------------|--------------|  
|COLUMN_TYPE|SQL_PARAM_INPUT または SQL_RESULT_COL|  
|序数|これは、結果セットの最後に返されるドライバー固有の列です。 列の SQL 型は整数です。|

