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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 29598ed97cba8be04a0c08727cffc40e663becba
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68063615"
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
  
## <a name="remarks"></a>解説  
 インデックスファイルは、REINDEX を発行するときに、設定された一意の設定を保持します。 詳細については、「 [INDEX](../../odbc/microsoft/index-command.md)」を参照してください。
