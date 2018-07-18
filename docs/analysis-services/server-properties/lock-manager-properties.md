---
title: ロック マネージャーのプロパティ |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 146bfef500424b7a587c3fb28616a3727086f265
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38033330"
---
# <a name="lock-manager-properties"></a>ロック マネージャーのプロパティ
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、次の表に示すロック マネージャー サーバー プロパティがサポートされています。 その他のサーバー プロパティとその設定方法の詳細については、「 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)」を参照してください。  
  
 **適用対象:** 多次元サーバー モードおよびテーブル サーバー モード  
  
## <a name="properties"></a>[プロパティ]  
 **DefaultLockTimeoutMS**  
 内部ロック要求の既定のロック タイムアウトをミリ秒単位で定義する、符号付き 32 ビット整数のプロパティです。  
  
 このプロパティの既定値は -1 であり、内部ロック要求をタイムアウトしないことを示します。  
  
 **LockWaitGranularityMS**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DeadlockDetectionGranularityMS**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Analysis Services インスタンスのサーバー モードの決定](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
