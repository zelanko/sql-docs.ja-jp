---
title: 正規の形式とパターン制限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- pattern restrictions
- canonical forms
ms.assetid: 088314ec-7d0b-4a05-8a33-f35da5bfe59c
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 61b11894a1fdcbcf29cba0f4ff4096cba041c71e
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "43888508"
---
# <a name="canonical-forms-and-pattern-restrictions"></a>正規の形式とパターン制限
  XSD パターン ファセットを使用すると、単純型の字句空間を制限できます。 複数の字句表現が可能であるような型にパターン制限を適用すると、一部の値が原因で検証時に予想外の動作が発生することがあります。  
  
 このような動作は、その値の字句表現がデータベースに格納されていないために発生します。 したがって、このような値は、出力としてシリアル化される際に、それぞれの正規表現に変換されます。 ドキュメントに含まれる値の正規の形式が型のパターン制限に準拠していない場合に、ユーザーがそのドキュメントの再挿入を試みると、そのドキュメントは拒否されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではこれを回避するために、再挿入できない値を含む XML ドキュメントはすべて、正規の形式がパターン制限に違反しているという理由で拒否します。 たとえば、値 "33.000" は、"33 **.0+" というパターン制限が指定されている** xs:decimal\\からの派生型に対して有効であると判断されません。 "33.000" はこのパターンに準拠していますが、正規の形式である "33" がパターンに違反しているためです。  
  
 そのため、注意が必要、プリミティブ型から派生した型にパターン ファセットを適用する場合: `boolean`、 `decimal`、 `float`、 `double`、 `dateTime`、 `time`、 `date`、 `hexBinary`、および`base64Binary`します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から警告が発行されます。  
  
 浮動小数点値の不正確なシリアル化にも同様の問題があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で使用されている浮動小数点のシリアル化アルゴリズムにより、近い値が同じ正規表現になることがあり得ます。 ただし、浮動小数点値がシリアル化され、再挿入される際に、その値がわずかに変化することがあります。 その結果、再挿入時にその型の **enumeration**、 **minInclusive**、 **minExclusive**、 **maxInclusive**、または **maxExclusive**の各ファセットに違反する値になることがまれにあります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではこれを回避するために、シリアル化や再挿入を行えない `xs:float` または `xs:double` から派生した値を拒否します。  
  
## <a name="see-also"></a>参照  
 [サーバー上の XML スキーマ コレクションの要件と制限](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
