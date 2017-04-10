---
title: "属性階層の (All) レベルの構成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "すべてのメンバー"
  - "IsAggregatable プロパティ"
  - "最上位レベル [Analysis Services]"
  - "(All) レベル"
  - "AttributeAllMemberName プロパティ"
  - "レベル [Analysis Services]"
  - "メンバー [Analysis Services], All"
  - "AllMemberName プロパティ"
ms.assetid: 0cb35e6f-b10f-483d-b893-78f6ca3979fd
caps.latest.revision: 33
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# 属性階層の (All) レベルの構成
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、(All) レベルはシステムによって生成されるオプションのレベルです。 このレベルには 1 つのメンバーが含まれ、その値は直下のレベルに含まれる全メンバーの値の集計です。 このメンバーを All メンバーと呼びます。 All メンバーはシステムによって生成されるメンバーで、ディメンション テーブルには含まれません。 (All) レベルのメンバーは階層の最上位にあるので、このメンバーの値は、階層内の全メンバーの値の集計値です。 通常、All メンバーは階層の既定メンバーとして機能します。  
  
 属性階層に (All) レベルがあるかどうかは属性の **IsAggregatable** プロパティ設定によって決まり、ユーザー定義階層に (All) レベルがあるかどうかはユーザー定義階層の最上位レベルに関する属性の **IsAggregatable** プロパティによって決まります。 **IsAggregatable** プロパティが **True** に設定されている場合は、(All) レベルが存在します。 **IsAggregatable** プロパティが **False** に設定されている場合は、階層に (All) レベルはありません。  
  
## 最上位レベルの設定  
 階層のレベルのソース属性で **IsAggregatable** プロパティが **False** に設定されている場合には、そのレベルより上の階層に集計レベルを表示できません。 非集計レベルは任意の階層の最上位レベルであるか、それより上のレベルのソース属性の **IsAggregatable** プロパティも **False** に設定する必要があります。  
  
## All メンバーと (All) レベル  
 (All) レベルの単一のメンバーは、All メンバーと呼ばれます。 ディメンションの **AttributeAllMemberName**プロパティにより、ディメンションの属性の All メンバーの名前が指定されます。 階層の **AllMemberName** プロパティにより、階層の All メンバーの名前が指定されます。  
  
## 参照  
 [既定のメンバーの定義](../../analysis-services/multidimensional-models/define-a-default-member.md)  
  
  