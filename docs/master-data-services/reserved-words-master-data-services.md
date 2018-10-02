---
title: 予約語 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
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
ms.openlocfilehash: 833c275846c3dde6d98542cf94b5c17f06fca16c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47698400"
---
# <a name="reserved-words-master-data-services"></a>予約語 (マスター データ サービス)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、モデル オブジェクトまたはメンバーを作成するときに使用できない単語がいくつかあります。 これらの単語を使用すると、エラーが発生する可能性があります。  
  
> [!NOTE]  
>  特殊文字 (記号、ハイフネーションなど) の使用も極力控えてください。  
  
-   [モデル](../master-data-services/reserved-words-master-data-services.md#models)  
  
-   [[エンティティ]](../master-data-services/reserved-words-master-data-services.md#entities)  
  
-   [明示的階層](../master-data-services/reserved-words-master-data-services.md#exhierarchies)  
  
-   [属性](../master-data-services/reserved-words-master-data-services.md#attributes)  
  
-   [メンバー](../master-data-services/reserved-words-master-data-services.md#members)  
  
##  <a name="models"></a> モデル  
 名前を **Name** または **Code**に設定したモデルを作成する場合は、 **[モデルと同じ名前のエンティティを作成する]** を選択しないでください。エンティティの名前に **Name** または **Code** は使用できません。  
  
##  <a name="entities"></a> [エンティティ]  
 エンティティ名には **Name** または **Code**を使用できません。  
  
##  <a name="exhierarchies"></a> 明示的階層  
 明示的階層名には **Name** または **Code**を使用できません。  
  
##  <a name="attributes"></a> 属性  
  
-   **ID**  
  
-   **Code**  
  
-   **EnterUserName**  
  
-   **LastChgUserName**  
  
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
 メンバーの場合、 **MDMMemberStatus**、 **MDMUnused**、または **ROOT** を **Code** 属性値として使用することはできません。  
  
## <a name="see-also"></a>参照  
 [マスター データ サービスの概要 (MDS)](../master-data-services/master-data-services-overview-mds.md)  
  
  
