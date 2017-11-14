---
title: "RDS チュートリアル |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 02/15/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDS tutorial [ADO]
ms.assetid: 6e3305a0-7bc7-40d1-9122-235c15d23ab2
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6cfb12781ca9e7387ea8016de581217ddf95f9c1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="rds-tutorial"></a>RDS チュートリアル
このチュートリアルでは、クエリおよびデータ ソースを更新する RDS プログラミング モデルを使用してを示します。 最初に、このタスクの実行に必要な手順をについて説明します。 このチュートリアルは Microsoft® Visual Basic Scripting Edition (ADO の Windows Foundation Class (ADO/WFC) を備えた) で繰り返されます。  
  
 このチュートリアルは、2 つの理由別の言語でコーディングされます。  
  
-   RDS のドキュメントには、Visual Basic ではリーダー コードが想定しています。 そのため、Visual Basic プログラマにとって便利ではあってもあまり役に立ちません他の言語を使用するプログラマにとってです。  
  
-   かどうか、特定の RDS 機能に関する不明なし、は少しわかっているとき、別の言語のことができますの別の言語で記述された同じ機能を検索して問題を解決します。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="how-the-tutorial-is-presented"></a>このチュートリアルの表示方法  
 このチュートリアルは、RDS プログラミング モデルに基づきます。 個別にプログラミング モデルの各手順についても説明します。 さらに、各ステップでは、Visual Basic コードのフラグメントを示します。  
  
 このコード例は、最小限の説明と他の言語で繰り返されます。 指定されたプログラミング言語のチュートリアルの各ステップは、プログラミング モデルとチュートリアルの説明で、対応する手順で示されます。 ステップの数を使用して、わかりやすいチュートリアルの説明を参照してください。  
  
 RDS のプログラミング モデルは、次のセクションで説明したようにします。 チュートリアルを続行するとロードマップとして使用します。  
  
## <a name="rds-programming-model-with-objects"></a>オブジェクトと RDS プログラミング モデル  
  
-   サーバーで、呼び出されるプログラムを指定し、クライアントから参照する方法 (プロキシ) を取得します。  
  
-   サーバーのプログラムを起動します。 データ ソースおよび発行するコマンドを識別するサーバーのプログラムにパラメーターを渡します。  
  
-   サーバーのプログラムを取得、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) ADO を使用して、通常、データ ソースからのオブジェクト。 必要に応じて、**レコード セット**オブジェクトは、サーバーで処理します。  
  
-   サーバーを返します、最終的な**レコード セット**をクライアント アプリケーションのオブジェクト。  
  
-   クライアントで、 **Recordset**オブジェクトは必要に応じてビジュアル コントロールで簡単に使用できるフォームに配置します。  
  
-   変更、 **Recordset**オブジェクトがサーバーに送信され、データ ソースを更新するために使用します。  
  
 このチュートリアルには、次のトピックが含まれています。  
  
-   [手順 1: サーバー プログラムを指定する (RDS チュートリアル)](../../../ado/guide/remote-data-service/step-1-specify-a-server-program-rds-tutorial.md)  
  
-   [手順 2: サーバー プログラムを呼び出す (RDS チュートリアル)](../../../ado/guide/remote-data-service/step-2-invoke-the-server-program-rds-tutorial.md)  
  
-   [手順 3: サーバーがレコード セットを取得する (RDS チュートリアル)](../../../ado/guide/remote-data-service/step-3-server-obtains-a-recordset-rds-tutorial.md)  
  
-   [手順 4: サーバーがレコード セットを返す (RDS チュートリアル)](../../../ado/guide/remote-data-service/step-4-server-returns-the-recordset-rds-tutorial.md)  
  
-   [手順 5: DataControl が使用可能になる (RDS チュートリアル)](../../../ado/guide/remote-data-service/step-5-datacontrol-is-made-usable-rds-tutorial.md)  
  
-   [手順 6: 変更がサーバーに送信される (RDS チュートリアル)](../../../ado/guide/remote-data-service/step-6-changes-are-sent-to-the-server-rds-tutorial.md)  
  
-   [RDS のチュートリアル (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)  
  
## <a name="see-also"></a>参照  
 [手順 1: サーバー プログラム (RDS チュートリアル) を指定します。](../../../ado/guide/remote-data-service/step-1-specify-a-server-program-rds-tutorial.md)   
 [RDS のチュートリアル (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   

