---
title: なのフルテキストインデックス、計算列は使用できません |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: cba737f7-b187-47d0-8458-23dc18d18aca
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: de153d45e2f652bfea6e9dce68428af84be68b6c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012342"
---
# <a name="full-text-indexes-on-nonpersisted-computed-columns-are-not-allowed"></a>保存されない計算列にフルテキスト インデックスを使用できない
  非決定的な計算列と不正確な計算列に対してフルテキスト インデックスを作成できません。 このような列は、型列やフルテキスト キー列として使用できません。  
  
## <a name="description"></a>説明  
 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] では、非決定的な計算列と不正確な計算列を型列やフルテキスト キー列として使用してフルテキスト インデックスを作成できます。 この機能はサポートされていません。 アップグレードすると、古くて互換性のない、サポート対象外のフルテキスト インデックスは無効になります。  
  
## <a name="corrective-action"></a>修正措置  
 このようなフルテキスト インデックスを有効にするには、列の定義を変更して決定的かつ正確にします。  
  
## <a name="see-also"></a>参照  
 [アップグレード アドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
