---
title: フルテキスト カタログ名の長さが 120 文字に制限されている |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs names
ms.assetid: 50633373-83f6-4ed9-99b9-71f92479a14f
caps.latest.revision: 22
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7f4312fe66072e9d06e664fee422b994dd9afb5b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37153743"
---
# <a name="length-of-full-text-catalog-names-restricted-to-120-characters"></a>フルテキスト カタログ名が最長 120 文字に制限されている
  フルテキスト カタログ名の長さが 120 文字に制限されており、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] における最大長 (128 文字) より文字数が少なくなっています。  
  
## <a name="description"></a>説明  
 この変更は既存のカタログ名には影響しません。ただし、120 文字よりも長い名前を持つフルテキスト カタログを作成するスクリプトはエラーになります。 カタログ名は、カタログに対応する論理ファイル名の生成に使用されます。  
  
## <a name="corrective-action"></a>修正措置  
 フルテキスト カタログを作成するすべてのスクリプトを変更し、カタログ名を 120 文字までにします。  
  
## <a name="see-also"></a>参照  
 [アップグレード アドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
