---
title: 予約語 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- reserved words [Master Data Services]
- Master Data Services, reserved words
ms.assetid: 88afd0d0-4362-4394-8357-4e65388fc0fc
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: cecb05cc93128baa31fea75ac0583f218d5dbe87
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140542"
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
 名前に設定したモデルを作成するかどうか**名前**、選択しないでください**モデルと同じ名前のエンティティを作成**ため**名前**エンティティの名前を使用することはできません。  
  
##  <a name="entities"></a> [エンティティ]  
 エンティティ名には **Name** または **Code**を使用できません。  
  
##  <a name="exhierarchies"></a> 明示的階層  
 明示的階層名には **Name** または **Code**を使用できません。  
  
##  <a name="attributes"></a> 属性  
  
-   **ID**  
  
-   **コード**  
  
-   **名前**  
  
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
  
  
