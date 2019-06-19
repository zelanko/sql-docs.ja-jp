---
title: SET UNIQUE コマンド |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET UNIQUE command [ODBC]
ms.assetid: 1f69e31e-4599-47cc-ac89-b86fba8703c5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f58eb771245b9820e27ca4d14c2f69035effa44
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63159315"
---
# <a name="set-unique-command"></a>SET UNIQUE コマンド
インデックス ファイルで、重複するインデックス キー値を持つレコードが保持されるかどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET UNIQUE ON | OFF  
```  
  
## <a name="arguments"></a>引数  
 ON  
 重複するインデックス キーの値を持つ任意のレコードは、インデックス ファイルに含まれないことを指定します。 インデックス ファイルには、元のインデックス キー値を持つ最初のレコードのみが含まれます。  
  
 OFF  
 (既定)。インデックス ファイルに重複するインデックス キー値を持つレコードが含まれることを指定します。  
  
## <a name="remarks"></a>コメント  
 インデックス ファイルでは、インデックスの再作成を発行するときに、設定の一意の設定が保持されます。 詳細については、次を参照してください。[インデックス](../../odbc/microsoft/index-command.md)します。
