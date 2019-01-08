---
title: 手順 5:更新パッケージのテスト |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 683e52e5-1c7e-49ab-9ffe-6a450a1c5776
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 52892e170d9825379dd21a0fdcedfedcaacd6ff7
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/13/2018
ms.locfileid: "53371994"
---
# <a name="step-5-testing-the-updated-packages"></a>手順 5:更新パッケージのテスト
  次のレッスンでは、目的のコンピューターにチュートリアル パッケージをインストールするときに使用する配置バンドルを作成しますが、その前にパッケージをテストする必要があります。 この作業では、Deployment Tutorial プロジェクトに追加して構成を拡張したパッケージ DataTransfer.dtsx および LoadXMLData を実行します。  
  
 パッケージを実行すると、パッケージ内の各実行ファイルが完了したときに緑色になります。 実行ファイルのすべてが緑色になると、パッケージの実行に成功したことを表します。 **[進行状況]** タブでパッケージ実行の進み具合を見ることもできます。  
  
 パッケージの実行に失敗した場合は、次のレッスンに進む前に修正する必要があります。  
  
### <a name="to-run-the-datatransfer-package"></a>DataTransfer パッケージを実行するには  
  
1.  ソリューション エクスプローラーで [DataTransfer.dtsx] をクリックします。  
  
2.  **[デバッグ]** メニューの **[デバッグ開始]** をクリックします。  
  
3.  パッケージの実行が完了したら、 **[デバッグ]** メニューの **[デバッグの停止]** をクリックします。  
  
### <a name="to-run-the-loadxmldata-package"></a>LoadXMLData パッケージを実行するには  
  
1.  ソリューション エクスプローラーで [LoadXMLData.dtsx] をクリックします。  
  
2.  **[デバッグ]** メニューの **[デバッグ開始]** をクリックします。  
  
3.  パッケージの実行が完了したら、 **[デバッグ]** メニューの **[デバッグの停止]** をクリックします。  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 2:配置バンドルを作成します。](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)  
  
![Integration Services のアイコン (小)](media/dts-16.gif "Integration Services アイコン (小)")**Integration Services の日付を維持します。**<br /> マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services のページを参照してください。](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。  
  
  
