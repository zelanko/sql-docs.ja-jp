---
title: スカラー関数エスケープシーケンス |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], scalar function
- scalar functions [ODBC], escape sequences
- ODBC escape sequences [ODBC], scalar function
ms.assetid: aaf5d516-e090-445f-8839-9e39581c69c7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8347b8e6f0fab6dffc5295fb3b8260a6a56ed123
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305075"
---
# <a name="scalar-function-escape-sequence"></a>スカラー関数のエスケープ シーケンス
ODBC は、スカラー関数にエスケープシーケンスを使用します。 このエスケープシーケンスの構文は次のとおりです。  
  
```  
{fn scalar-function}  
```  
  
## <a name="remarks"></a>解説  
 BNF 表記では、構文は次のとおりです。  
  
 *ODBC スカラー関数エスケープ*::=  
  
 *ODBC-esc-イニシエーター* fn*スカラー関数 ODBC-esc-終端文字*  
  
 *スカラー関数*::=*関数名*(*引数リスト*)  
  
 (非端末*関数名および関数名*(*引数リスト*) の定義は[、「付録 E: スカラー関数](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)」のスカラー関数のリストから派生しています。 *function-name*  
  
 *ODBC-esc-イニシエーター* ::= {  
  
 *ODBC-esc 終止符*::= }  
  
 データ ソースがプロシージャをサポートし、ドライバーが ODBC プロシージャ呼び出し構文をサポートしているかどうかを確認するには、アプリケーションは**SQLGetInfo**を呼び出すことができます。 詳細については、「[付録 E: スカラー関数](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)」を参照してください。
