---
title: SQLTransact (Access ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLTransact
- SQLTransact function [ODBC], Access Driver
ms.assetid: 892b79c7-9e20-4d1f-bc60-d4b25694ca25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b0cb17ed043a6b533b007769b9cbb28652d06e6f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63061651"
---
# <a name="sqltransact-access-driver"></a>SQLTransact (Access ドライバー)
> [!NOTE]  
>  このトピックでは、Access ドライバー固有の情報を提供します。 この関数の詳細については、該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)します。  
  
 Microsoft Access ドライバーを使用すると、ときに指定してと SQL_ROLLBACK はサポートされて、 *fType*への呼び出しで引数**SQLTransact**します。  
  
 や REPAIR_DB キーワードを使用して Microsoft Access ドライバーのセットアップには、データベースの修復オプションを使用して、影響を受けたデータベースを修復できるコミット処理中にエラーが発生した場合、 **SQLConfigDataSource**関数。
