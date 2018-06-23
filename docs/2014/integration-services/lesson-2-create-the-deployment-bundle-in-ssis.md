---
title: 'レッスン 2: 配置バンドルを作成する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab17289d-c3d4-4a5e-b7f5-4fea8ae21707
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 91852a7af945b1e381008db91776476bdcff0aa9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083223"
---
# <a name="lesson-2-creating-the-deployment-bundle"></a>レッスン 2: 配置バンドルの作成
  [「レッスン 1: 配置バンドルを作成する準備」](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md)では、Deployment Tutorial という名前の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを作成し、パッケージとサポート ファイルをプロジェクトに追加して、パッケージに構成を実装しました。  
  
 このレッスンでは、配置バンドルを作成します。配置バンドルとは、他のコンピューターにパッケージをインストールするために必要なアイテムが含まれているフォルダーです。 配置バンドルには、Deployment Tutorial プロジェクトの配置マニフェスト、パッケージのコピー、サポート ファイルのコピーを含めます。 配置マニフェストとは、配置バンドルに含まれているパッケージ、その他のファイル、および構成の一覧です。  
  
 また、配置バンドルに含まれているファイルの一覧を確認し、マニフェストの内容を確認します。  
  
 **このレッスンの推定所要時間:** 30 分  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
 このレッスンの内容は次のとおりです。  
  
-   [手順 1: 配置ユーティリティの構築](../integration-services/lesson-2-1-building-the-deployment-utility.md)  
  
-   [手順 2: 配置バンドルの確認](../integration-services/lesson-2-2-verifying-the-deployment-bundle.md)  
  
## <a name="start-the-lesson"></a>レッスンの開始  
 [手順 1: 配置ユーティリティの構築](../integration-services/lesson-2-1-building-the-deployment-utility.md)  
  
![Integration Services のアイコン (小)](media/dts-16.gif "Integration Services アイコン (小)")**Integration Services と終了日を維持** <br /> マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services のページを参照してください。](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。  
  
  