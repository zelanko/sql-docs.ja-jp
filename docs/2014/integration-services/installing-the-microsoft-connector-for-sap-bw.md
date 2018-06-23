---
title: Microsoft Connector 1.1 for SAP BW のインストール |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: dc6bbbf5972615880d3852d5f56a955862c9f22b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178032"
---
# <a name="installing-the-microsoft-connector-for-11-sap-bw"></a>Microsoft Connector 1.1 for SAP BW のインストール
  インストールする、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW およびそのドキュメントをダウンロードして、SQL Server 機能パック Web ページから Windows インストーラー パッケージを実行します。  
  
> [!IMPORTANT]  
>  Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。 SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。  
  
> [!IMPORTANT]  
>  SAP Netweaver BW からデータを抽出するには、追加の SAP のライセンスが必要です。 これらの要件を確認するには、SAP にお問い合わせください。  
  
## <a name="required-sap-files"></a>必要な SAP のファイル  
 使用する、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW、されませんが、ローカル コンピューターで、SAP フロント エンド ソフトウェア (SAP GUI) をインストールします。  
  
 ただし、SAP の .NET コネクタ ファイルである librfc32.dll を、Windows フォルダー内の system サブフォルダーにコピーする必要があります (通常は、このフォルダーの場所は、 **C:\Windows\system32**です)。  
  
## <a name="considerations-for-64-bit-computers"></a>64 ビット コンピューターに関する注意事項  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW は、64 ビット バージョンを完全にサポート[!INCLUDE[msCoName](../includes/msconame-md.md)]Windows です。 64 ビット コンピューターで、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW は、次の追加要件。  
  
-   任意の 64 ビット Windows オペレーティング システムで、パッケージを 64 ビット モードで実行するには、SAP GUI ファイルの 64 ビット バージョンである librfc32.dll を、Windows フォルダー内の **system32** フォルダーにコピーします (通常は、このファイルの場所は、 **C:\Windows\system32**です)。  
  
-   任意の 64 ビット Windows オペレーティング システムで、パッケージを 32 ビット モードで実行するには、SAP GUI ファイルである librfc32.dll を、Windows フォルダー内の **SysWow64** フォルダーにコピーします (通常は、このフォルダーの場所は、 **C:\Windows\SysWow64**です)。  
  
  