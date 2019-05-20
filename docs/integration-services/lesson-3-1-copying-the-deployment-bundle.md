---
title: 手順 1:配置バンドルのコピー | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: b6ef1e56-d278-4a24-afd3-68d8e0595cbb
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 153975d4b2a418c694188ca30c0ddb9fc19b0fc8
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2019
ms.locfileid: "65722387"
---
# <a name="lesson-3-1---copying-the-deployment-bundle"></a>レッスン 3-1 - 配置バンドルのコピー

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


このタスクでは、配置先コンピューターに配置バンドルをコピーします。  
  
配置先コンピューターに配置バンドルをコピーするには、まず配置先コンピューターにパブリック共有を作成し、ドライブをパブリック共有にマッピングして、配置バンドルを共有にコピーするのが最も簡単な方法です。 パブリック フォルダーを作成して構成する方法や、ドライブのマッピング方法がわからない場合は、Windows のドキュメントを参照してください。  
  
### <a name="to-copy-the-deployment-bundle"></a>配置バンドルをコピーするには  
  
1.  コンピューターで配置バンドルを探します。  
  
    既定の場所を使用した場合、配置バンドルは Deployment Tutorial フォルダーの Bin\Deployment フォルダーにあります。  
  
2.  Deployment フォルダーを右クリックし、**[コピー]** をクリックします。  
  
3.  ターゲット コンピューターで、フォルダーをコピーするパブリック共有を探し、**[貼り付け]** をクリックします。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[手順 2:パッケージ インストール ウィザードの実行](../integration-services/lesson-3-2-running-the-package-installation-wizard.md)  
  
  
  
