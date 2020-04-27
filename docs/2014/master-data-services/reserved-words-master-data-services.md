---
title: 予約語 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- reserved words [Master Data Services]
- Master Data Services, reserved words
ms.assetid: 88afd0d0-4362-4394-8357-4e65388fc0fc
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 5435c2a48417156abd6d4f831bf61c9ba6440fab
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "65482580"
---
# <a name="reserved-words-master-data-services"></a>予約語 (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、モデル オブジェクトまたはメンバーを作成するときに使用できない単語がいくつかあります。 これらの単語を使用すると、エラーが発生する可能性があります。  
  
> [!NOTE]  
>  特殊文字 (記号、ハイフネーションなど) の使用も極力控えてください。  
  
-   [モデル](#models)  
  
-   [エンティティ](#entities)  
  
-   [明示的階層](#exhierarchies)  
  
-   [属性](#attributes)  
  
-   [メンバー](#members)  
  
##  <a name="models"></a><a name="models"></a>モジュール  
 名前を "**名前**" に設定したモデルを作成する場合は、[**モデルと同じ名前のエンティティを作成**する] を選択しないでください。エンティティの名前には**名前**を使用できません。  
  
##  <a name="entities"></a><a name="entities"></a>事業  
 エンティティ名には **Name** または **Code**を使用できません。  
  
##  <a name="explicit-hierarchies"></a><a name="exhierarchies"></a>明示的階層  
 明示的階層名には **Name** または **Code**を使用できません。  
  
##  <a name="attributes"></a><a name="attributes"></a>アトリビュート  
  
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
  
##  <a name="members"></a><a name="members"></a>属する  
 メンバーの場合、 **Code**属性値に**MDMMemberStatus**または**ROOT**を使用することはできません。  
  
## <a name="see-also"></a>参照  
 [マスター データ サービス概要](master-data-services-overview-mds.md)  
  
  
