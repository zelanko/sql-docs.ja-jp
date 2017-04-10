---
title: "Microsoft Connector for SAP BW のインストール | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
caps.latest.revision: 11
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 11
---
# Microsoft Connector for SAP BW のインストール
  [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector for SAP BW for SQL Server 2016 は、SQL Server 2016 の Feature Pack のコンポーネントです。 Connector for SAP BW およびそのドキュメントをインストールするには、 [SQL Server 2016 Feature Pack Web ページ](http://go.microsoft.com/fwlink/?LinkId=746297)からインストーラーをダウンロードして実行します。  
  
> [!IMPORTANT]  
>  Microsoft Connector for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。 SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。  
  
> [!IMPORTANT]  
>  SAP Netweaver BW からデータを抽出するには、追加の SAP のライセンスが必要です。 これらの要件を確認するには、SAP にお問い合わせください。  
  
## 必要な SAP のファイル  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector for SAP BW を使用するために、SAP フロント エンド ソフトウェア (SAP GUI) をローカル コンピューターにインストールする必要はありません。  
  
 ただし、SAP の .NET コネクタ ファイルである librfc32.dll を、Windows フォルダー内の system サブフォルダーにコピーする必要があります (通常は、このフォルダーの場所は、**C:\Windows\system32** です)。  
  
## 64 ビット コンピューターに関する注意事項  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector for SAP BW は、[!INCLUDE[msCoName](../includes/msconame-md.md)] Windows の 64 ビット バージョンを完全サポートしています。 64 ビット コンピューターでは、[!INCLUDE[msCoName](../includes/msconame-md.md)] Connector for SAP BW に次の要件があります。  
  
-   任意の 64 ビット Windows オペレーティング システムで、パッケージを 64 ビット モードで実行するには、SAP GUI ファイルの 64 ビット バージョンである librfc32.dll を、Windows フォルダー内の **system32** フォルダーにコピーします (通常は、このファイルの場所は、**C:\Windows\system32** です)。  
  
-   任意の 64 ビット Windows オペレーティング システムで、パッケージを 32 ビット モードで実行するには、SAP GUI ファイルである librfc32.dll を、Windows フォルダー内の **SysWow64** フォルダーにコピーします (通常は、このフォルダーの場所は、**C:\Windows\SysWow64** です)。  
  
  