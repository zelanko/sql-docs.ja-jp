---
title: フルテキスト カタログ名の長さが 120 文字に制限されている |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- full-text catalogs names
ms.assetid: 50633373-83f6-4ed9-99b9-71f92479a14f
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f11c8b5a0698c83846f1570946a551f82a09ab48
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175264"
---
# <a name="length-of-full-text-catalog-names-restricted-to-120-characters"></a>フルテキスト カタログ名が最長 120 文字に制限されている
  フルテキスト カタログ名の長さが 120 文字に制限されており、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] における最大長 (128 文字) より文字数が少なくなっています。  
  
## <a name="description"></a>説明  
 この変更は既存のカタログ名には影響しません。ただし、120 文字よりも長い名前を持つフルテキスト カタログを作成するスクリプトはエラーになります。 カタログ名は、カタログに対応する論理ファイル名の生成に使用されます。  
  
## <a name="corrective-action"></a>修正措置  
 フルテキスト カタログを作成するすべてのスクリプトを変更し、カタログ名を 120 文字までにします。  
  
## <a name="see-also"></a>参照  
 [アップグレード アドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  