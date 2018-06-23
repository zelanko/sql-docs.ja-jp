---
title: 予約語 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- reserved words [Master Data Services]
- Master Data Services, reserved words
ms.assetid: 88afd0d0-4362-4394-8357-4e65388fc0fc
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 3307fb8185abfb6b862e72691596e4385b09dcb8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178244"
---
# <a name="reserved-words-master-data-services"></a>予約語 (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、モデル オブジェクトまたはメンバーを作成するときに使用できない単語がいくつかあります。 これらの単語を使用すると、エラーが発生する可能性があります。  
  
> [!NOTE]  
>  特殊文字 (記号、ハイフネーションなど) の使用も極力控えてください。  
  
-   [モデル](#models)  
  
-   [エンティティ](#entities)  
  
-   [明示的階層](#exhierarchies)  
  
-   [Attributes](#attributes)  
  
-   [メンバー](#members)  
  
##  <a name="models"></a> モデル  
 名に設定したモデルを作成するかどうか**名前**を選択しない**モデルと同じ名前のエンティティを作成する**ため**名前**エンティティの名前は使用できません。  
  
##  <a name="entities"></a> [エンティティ]  
 エンティティ名には **Name** または **Code**を使用できません。  
  
##  <a name="exhierarchies"></a> 明示的階層  
 明示的階層名には **Name** または **Code**を使用できません。  
  
##  <a name="attributes"></a> 属性  
  
-   **ID**  
  
-   **コード**  
  
-   **Name**  
  
-   **EnterDTM**  
  
-   **EnterUserID**  
  
-   **EnterUserName**  
  
-   **LastChgDTM**  
  
-   **LastChgUserID**  
  
-   **Status_ID**  
  
-   **ValidationStatus_ID**  
  
-   **Version_ID**  
  
##  <a name="members"></a> メンバー  
 使用することはできません、メンバーの**MDMMemberStatus**または**ルート**の**コード**属性の値。  
  
## <a name="see-also"></a>参照  
 [マスター データ サービス概要](master-data-services-overview-mds.md)  
  
  