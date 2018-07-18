---
title: '手順 1: 配置バンドルのコピー | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b6ef1e56-d278-4a24-afd3-68d8e0595cbb
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a63c3fa3744d84014405376b36df4a1eb5d7a583
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37318804"
---
# <a name="step-1-copying-the-deployment-bundle"></a>手順 1: 配置バンドルのコピー
  このタスクでは、配置先コンピューターに配置バンドルをコピーします。  
  
 配置先コンピューターに配置バンドルをコピーするには、まず配置先コンピューターにパブリック共有を作成し、ドライブをパブリック共有にマッピングして、配置バンドルを共有にコピーするのが最も簡単な方法です。 パブリック フォルダーを作成して構成する方法や、ドライブのマッピング方法がわからない場合は、Windows のドキュメントを参照してください。  
  
### <a name="to-copy-the-deployment-bundle"></a>配置バンドルをコピーするには  
  
1.  コンピューターで配置バンドルを探します。  
  
     既定の場所を使用した場合、配置バンドルは Deployment Tutorial フォルダーの Bin\Deployment フォルダーにあります。  
  
2.  Deployment フォルダーを右クリックし、[ **コピー**] をクリックします。  
  
3.  配置先のコンピューターで、フォルダーをコピーするパブリック共有を探し、[ **貼り付け**] をクリックします。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [手順 2: パッケージ インストール ウィザードの実行](../integration-services/lesson-3-2-running-the-package-installation-wizard.md)  
  
![Integration Services のアイコン (小)](media/dts-16.gif "Integration Services アイコン (小)")**Integration Services の日付を維持します。  **<br /> マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services のページを参照してください。](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。  
  
  
