---
title: "[Web サービス タスク エディター] ([全般] ページ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.webservicestask.general.f1"
helpviewer_keywords: 
  - "Web サービス タスク エディター"
ms.assetid: 4d7df283-430d-4f0f-9dd4-5909554cd5eb
caps.latest.revision: 34
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 34
---
# [Web サービス タスク エディター] ([全般] ページ)
  **[Web サービス タスク エディター]** ダイアログ ボックスの **[全般]** ページを使用すると、HTTP 接続マネージャーの指定、Web サービス タスクで使用する WSDL (Web サービス記述言語) ファイルの場所の指定、Web サービス タスクの記述、WSDL ファイルのダウンロードなどの操作を実行できます。  
  
 このタスクの詳細については、「[Web サービス タスク](../../integration-services/control-flow/web-service-task.md)」を参照してください。  
  
## オプション  
 **[HTTPConnection]**  
 接続マネージャーを一覧から選択するか、**[新しい接続]** をクリックして新しい接続マネージャーを作成します。  
  
> [!IMPORTANT]  
>  HTTP 接続マネージャーでは、匿名認証と基本認証のみがサポートされています。 Windows 認証はサポートされていません。  
  
 **関連項目:**  [HTTP 接続マネージャー](../../integration-services/connection-manager/http-connection-manager.md), 、[[HTTP 接続マネージャー エディター] ([サーバー] ページ)](../Topic/HTTP%20Connection%20Manager%20Editor%20\(Server%20Page\).md)  
  
 **[WSDLFile]**  
 コンピューターのローカルにある WSDL ファイルの完全修飾パスを入力するか、参照ボタン (**[...]**) をクリックしてファイルを指定します。  
  
 WSDL ファイルを既に手動でコンピューターにダウンロードしている場合は、そのファイルを選択します。 ただし、WSDL ファイルをまだダウンロードしていない場合は、次の手順に従います。  
  
-   ファイル名拡張子が ".wsdl" の空のファイルを作成します。  
  
-   **[WSDLFile]** オプションで、この空のファイルを選択します。  
  
-   **[OverwriteWSDLFile]** の値を **True** に設定して、空のファイルを実際の WSDL ファイルで上書きできるようにします。  
  
-   **[WSDL のダウンロード]** をクリックして実際の WSDL ファイルをダウンロードし、空のファイルを上書きします。  
  
    > [!NOTE]  
    >  **[WSDL のダウンロード]** オプションは、**[WSDLFile]** ボックスに既存のローカル ファイルの名前を指定するまで有効になりません。  
  
 **[OverwriteWSDLFile]**  
 Web サービス タスクの WSDL ファイルを上書きできるかどうかを示します。  
  
 **[WSDL のダウンロード]** ボタンを使用して WSDL ファイルをダウンロードする場合は、この値を **True**に設定します。  
  
 **名前**  
 Web サービス タスクの一意な名前を指定します。 この名前は、タスク アイコンのラベルとして使用されます。  
  
> [!NOTE]  
>  タスク名はパッケージ内で一意である必要があります。  
  
 **Description**  
 Web サービス タスクの説明を入力します。  
  
 **[WSDL のダウンロード]**  
 WSDL ファイルをダウンロードします。  
  
 このボタンは、 **[WSDLFile]** ボックスに既存のローカル ファイルの名前を指定するまで有効になりません。  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [[Web サービス タスク エディター] ([入力] ページ)](../Topic/Web%20Service%20Task%20Editor%20\(Input%20Page\).md)   
 [[Web サービス タスク エディター] ([出力] ページ)](../Topic/Web%20Service%20Task%20Editor%20\(Output%20Page\).md)   
 [[式] ページ](../Topic/Expressions%20Page.md)  
  
  