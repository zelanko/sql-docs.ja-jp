---
title: "固定属性と変化する属性のオプション (緩やかに変化するディメンション ウィザード) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.loaddimwizard.attriboption.f1
ms.assetid: c841345c-7d03-452f-9379-1c8c464f029c
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ff9390dbf0831673d7eca28e896a2ca2c61ead6a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="fixed-and-changing-attribute-options-slowly-changing-dimension-wizard"></a>[固定属性と変化する属性のオプション] (緩やかに変化するディメンション ウィザード)
  **[固定属性と変化する属性のオプション]** ダイアログ ボックスを使用すると、固定属性と変化する属性において変更に応答する方法を指定します。  
  
 このウィザードの詳細については、「 [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[固定属性]**  
 固定属性の場合は、固定属性で変更が検出された場合に、タスクが失敗するかどうかを示します。  
  
 **[変化する属性]**  
 変化する属性の場合は、変化する属性で変更が検出された場合に、現在のレコードに加え、古いレコードや有効期限が切れたレコードをタスクが変更するかどうかを指定します。 有効期限が切れたレコードとは、履歴属性の変更 (種類 2 の変更) によって新しいレコードに置き換えられたレコードのことです。 このオプションを選択すると、リレーショナル データ ウェアハウスで構築された多次元オブジェクトに処理要件が追加される可能性があります。  
  
## <a name="see-also"></a>参照  
 [緩やかに変化するディメンション ウィザードを使用して出力を構成する](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
