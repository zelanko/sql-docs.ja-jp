---
title: '手順 5: 更新したパッケージのテスト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 683e52e5-1c7e-49ab-9ffe-6a450a1c5776
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 7db13e319b07a605172746a650c0292dc7f2bfd8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074912"
---
# <a name="step-5-testing-the-updated-packages"></a>手順 5: 更新したパッケージのテスト
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
 [レッスン 2: 配置バンドルの作成](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)  
  
![Integration Services のアイコン (小)](media/dts-16.gif "Integration Services アイコン (小)")**Integration Services と終了日を維持** <br /> マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services のページを参照してください。](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。  
  
  