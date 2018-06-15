---
title: 一意の SET コマンド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SET UNIQUE command [ODBC]
ms.assetid: 1f69e31e-4599-47cc-ac89-b86fba8703c5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d824d02186601f2afcc60059aad40cf469ff98c4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32900955"
---
# <a name="set-unique-command"></a>セットの一意のコマンド
インデックス ファイルに重複するインデックス キー値を持つレコードが保持されるかどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET UNIQUE ON | OFF  
```  
  
## <a name="arguments"></a>引数  
 ON  
 重複するインデックスのキー値を持つ任意のレコードは、インデックス ファイルに含まれないことを指定します。 インデックス ファイルには、元のインデックス キー値を持つ最初のレコードだけが含まれます。  
  
 OFF  
 (既定)。インデックス ファイルに重複するインデックス キー値を持つレコードが含まれることを指定します。  
  
## <a name="remarks"></a>解説  
 インデックス ファイルでは、インデックスの再作成を発行したときに、その一意の設定の設定が保持されます。 詳細については、次を参照してください。[インデックス](../../odbc/microsoft/index-command.md)です。
