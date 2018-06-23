---
title: 'レッスン 2: Web 参照の追加 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2c2b8b8-6b13-45ca-ab3b-1582447b6807
caps.latest.revision: 29
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: ff574cf6ab00b4b368a7d372957b2348757ad0f5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163982"
---
# <a name="lesson-2-adding-a-web-reference"></a>レッスン 2 : Web 参照の追加
  Web サービスの探索とは、クライアントが Web サービスを検索し、そのサービス記述を取得する処理です。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] の Web サービス探索処理では、事前に定義されたアルゴリズムに従って、Web サイトの問い合わせが行われます。 この処理の目的はサービス記述を見つけることです。サービス記述とは、WSDL (Web サービス記述言語) を使用する XML ドキュメントです。  
  
 サービス記述には、利用可能なサービスとこれらのサービスとの対話方法が記述されています。 サービス記述がない場合は、プログラムから Web サービスと対話することはできません。  
  
 アプリケーションには、Web サービスと通信する方法とランタイムで Web サービスを検出する方法を実装する必要があります。 これを実現するには、プロジェクトに Web サービス用の Web 参照を追加します。その結果、プロキシ クラスが生成されます。プロキシ クラスは、Web サービスとのインターフェイスとなり、Web サービスのローカル表記を提供します。 詳細については、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ドキュメントの「方法 : XML Web サービス プロキシを生成する」を参照してください。  
  
### <a name="to-add-a-web-reference"></a>Web 参照を追加するには  
  
1.  **プロジェクト** メニューのをクリックして**サービス参照の追加**です。  
  
2.  **サービス参照の追加**ダイアログ ボックスで、をクリックして**詳細**です。  
  
3.  **サービス参照設定**ダイアログ ボックスで、をクリックして**Web 参照の追加**です。  
  
4.  **URL**のボックス、 **Web 参照の追加** ダイアログ ボックスに入力など、レポート サーバー Web サービスのサービスの説明を取得する URL、http://localhost/reportserver/reportservice2010.asmxです。 をクリックして、**移動**ボタン、Web サービスに関する情報を取得します。  
  
     \- または -  
  
     クリックして、レポート サーバー Web サービスがローカル コンピューター上に存在する場合、**ローカル マシン上のサービスを Web**ブラウザー ウィンドウでリンクします。 次に、表示された一覧から ReportService2010 Web サービスのリンクをクリックします。  
  
5.  **Web 参照名**ボックスで、これはこの Web 参照に使用する名前空間を ReportService2010 に Web 参照の名前を変更します。  
  
6.  をクリックして**参照の追加**対象の Web サービスに Web 参照を追加します。  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] により、サービス記述がダウンロードされ、アプリケーションとレポート サーバー Web サービス間のインターフェイスとなるプロキシ クラスが生成されます。 また、Web 参照が動作するように、<xref:System.Web.Services> 名前空間への参照を追加する必要があります。  
  
7.  [プロジェクト] メニューをクリックして**参照の追加**です。  
  
8.  **参照の追加** ダイアログ ボックスで、 **.NET**  タブで、 **System.Web.Services**をクリックし、 **ok**です。  
  
 詳細については、「[SOAP API へのアクセス](../reporting-services/report-server-web-service/accessing-the-soap-api.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [レポート サーバー Web サービス](../reporting-services/report-server-web-service/report-server-web-service.md)   
 [レッスン 3: Web サービスへのアクセス](../../2014/tutorials/lesson-3-accessing-the-web-service.md)   
 [Visual Basic または Visual C を使用してレポート サーバー Web サービスにアクセスする&#35; &#40;SSRS チュートリアル&#41;](../../2014/tutorials/access-report-server-web-service-vb-vcsharp-ssrs-tutorial.md)  
  
  