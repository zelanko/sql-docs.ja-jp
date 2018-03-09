---
title: "スカラー関数エスケープ シーケンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- escape sequences [ODBC], scalar function
- scalar functions [ODBC], escape sequences
- ODBC escape sequences [ODBC], scalar function
ms.assetid: aaf5d516-e090-445f-8839-9e39581c69c7
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6792312d9b82b54460a35dd6f614c206c7bdfe3d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="scalar-function-escape-sequence"></a>スカラー関数エスケープ シーケンス
ODBC スカラー関数のエスケープ シーケンスを使用します。 このエスケープ シーケンスの構文は次のとおりです。  
  
```  
{fn scalar-function}  
```  
  
## <a name="remarks"></a>解説  
 BNF 表記で、構文のとおりです。  
  
 *ODBC スカラー関数エスケープ*:: =  
  
 *ODBC esc イニシエーター* fn*スカラー関数 ODBC esc ターミネータ*  
  
 *スカラー関数*:: =*関数名*(*引数リスト*)  
  
 (、非終端要素の定義*関数名*と*関数名*(*引数リスト*) スカラー関数の一覧から派生した[「付録 e: スカラー関数は](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md))。  
  
 *ODBC esc イニシエーター* :: = {  
  
 *Esc 終端の ODBC* :: =}  
  
 アプリケーションが呼び出すことができます、データ ソースには、プロシージャがサポートしていて、ドライバーは ODBC のプロシージャの呼び出し構文をサポートするかどうかを調べるに**SQLGetInfo**です。 詳細については、次を参照してください。[付録 e: のスカラー関数](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)です。
