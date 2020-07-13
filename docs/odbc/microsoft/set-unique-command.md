---
title: UNIQUE コマンドの設定 |Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7d3d37509450d1305891100b37bfd1ad026166e8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300842"
---
# <a name="set-unique-command"></a>SET UNIQUE コマンド
重複するインデックスキー値を持つレコードをインデックスファイルで保持するかどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET UNIQUE ON | OFF  
```  
  
## <a name="arguments"></a>引数  
 ON  
 重複するインデックスキー値を持つすべてのレコードをインデックスファイルに含めないように指定します。 インデックスファイルには、元のインデックスキー値を持つ最初のレコードだけが含まれます。  
  
 OFF  
 (既定値)。重複するインデックスキー値を持つレコードをインデックスファイルに含めることを指定します。  
  
## <a name="remarks"></a>Remarks  
 インデックスファイルは、REINDEX を発行するときに、設定された一意の設定を保持します。 詳細については、「 [INDEX](../../odbc/microsoft/index-command.md)」を参照してください。
