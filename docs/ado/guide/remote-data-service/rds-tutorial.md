---
title: RDS チュートリアル |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO]
ms.assetid: 6e3305a0-7bc7-40d1-9122-235c15d23ab2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f9a7538bb51ebe0a04a20aff81e83c3cc1ac92aa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47747890"
---
# <a name="rds-tutorial"></a>RDS チュートリアル
このチュートリアルでは、RDS のプログラミング モデルを使用して、データ ソースの更新とクエリを示しています。 最初に、このタスクの実行に必要な手順をについて説明します。 このチュートリアルは Microsoft® Visual Basic Scripting Edition (ADO の Windows Foundation Class (ADO と WFC) を備えた) で繰り返されます。  
  
 このチュートリアルは異なる言語でコーディングして 2 つの理由。  
  
-   RDS のドキュメントには、Visual Basic では、リーダーのコードが想定しています。 これにより、ドキュメントの Visual Basic プログラマにとって便利ではあってもあまり役に立ちません他の言語を使用するプログラマにとって。  
  
-   少しがわかっていて、特定の RDS 機能について不明な別の言語のあります別の言語で記述された同じ機能を探すことによって問題を解決します。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 以降、RDS サーバー コンポーネントに含まれていない、Windows オペレーティング システム (Windows 8 を参照してくださいと[Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)の詳細)。 RDS クライアント コンポーネントは、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)します。  
  
## <a name="how-the-tutorial-is-presented"></a>このチュートリアルを表示する方法  
 このチュートリアルは、RDS のプログラミング モデルに基づきます。 個別にプログラミング モデルの各手順について説明します。 さらに、各ステップでは、Visual Basic のコードの一部を示しています。  
  
 コード例は、最小限のディスカッションで他の言語で繰り返されます。 指定されたプログラミング言語のチュートリアルでは、各ステップは、プログラミング モデルとチュートリアルの説明で、対応する手順でマークされます。 ステップの番号を使用して、わかりやすいチュートリアルの説明を参照してください。  
  
 RDS のプログラミング モデルは、次のセクションに記載されています。 チュートリアルを続行すると、ロードマップとして使用します。  
  
## <a name="rds-programming-model-with-objects"></a>RDS のプログラミング モデルとオブジェクト  
  
-   サーバーで、呼び出されるプログラムを指定し、クライアントから参照する方法 (プロキシ) を取得します。  
  
-   サーバー プログラムを起動します。 データ ソースおよび発行するコマンドを識別するサーバーのプログラムには、パラメーターを渡します。  
  
-   サーバーのプログラムを取得、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)ADO を使用して、通常、データ ソースからのオブジェクト。 必要に応じて、**レコード セット**オブジェクトは、サーバーで処理します。  
  
-   サーバーを返します、最終的な**レコード セット**をクライアント アプリケーションのオブジェクト。  
  
-   クライアントで、 **Recordset**オブジェクトは、必要に応じてビジュアル コントロールで簡単に使用できるフォームに配置します。  
  
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
