---
title: 永続化されない、計算列でフルテキスト インデックスは許可されません |Microsoft ドキュメント
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
- full-text indexes
ms.assetid: cba737f7-b187-47d0-8458-23dc18d18aca
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d51500dca40ed039816b973cb4698971996e2b01
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165513"
---
# <a name="full-text-indexes-on-nonpersisted-computed-columns-are-not-allowed"></a>保存されない計算列にフルテキスト インデックスを使用できない
  非決定的な計算列と不正確な計算列に対してフルテキスト インデックスを作成できません。 このような列は、型列やフルテキスト キー列として使用できません。  
  
## <a name="description"></a>説明  
 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] では、非決定的な計算列と不正確な計算列を型列やフルテキスト キー列として使用してフルテキスト インデックスを作成できます。 この機能はサポートされません。 アップグレードすると、古くて互換性のない、サポート対象外のフルテキスト インデックスは無効になります。  
  
## <a name="corrective-action"></a>修正措置  
 このようなフルテキスト インデックスを有効にするには、列の定義を変更して決定的かつ正確にします。  
  
## <a name="see-also"></a>参照  
 [アップグレード アドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  