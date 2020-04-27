---
title: Microsoft Connector for 1.1 SAP BW のインストール |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0e43a45f9b21e631638dec43a8a126b4f007429d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62767754"
---
# <a name="installing-the-microsoft-connector-for-11-sap-bw"></a>Microsoft Connector 1.1 for SAP BW のインストール
  SAP BW とその[!INCLUDE[msCoName](../includes/msconame-md.md)]ドキュメントのコネクタ1.1 をインストールするには、SQL Server Feature Pack Web ページから Windows インストーラーパッケージをダウンロードして実行します。  
  
> [!IMPORTANT]  
>  Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。 SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。  
  
> [!IMPORTANT]  
>  SAP Netweaver BW からデータを抽出するには、追加の SAP のライセンスが必要です。 これらの要件を確認するには、SAP にお問い合わせください。  
  
## <a name="required-sap-files"></a>必要な SAP のファイル  
 SAP BW に[!INCLUDE[msCoName](../includes/msconame-md.md)]コネクタ1.1 を使用するには、Sap フロントエンドソフトウェア (sap GUI) をローカルコンピューターにインストールする必要はありません。  
  
 ただし、SAP の .NET コネクタ ファイルである librfc32.dll を、Windows フォルダー内の system サブフォルダーにコピーする必要があります (通常は、このフォルダーの場所は、 **C:\Windows\system32**です)。  
  
## <a name="considerations-for-64-bit-computers"></a>64 ビット コンピューターに関する注意事項  
 コネクタ[!INCLUDE[msCoName](../includes/msconame-md.md)] 1.1 for SAP BW は、Windows の[!INCLUDE[msCoName](../includes/msconame-md.md)] 64 ビットバージョンを完全にサポートしています。 64ビットコンピューターの場合、SAP BW の[!INCLUDE[msCoName](../includes/msconame-md.md)]コネクタ1.1 には、次の追加要件があります。  
  
-   任意の 64 ビット Windows オペレーティング システムで、パッケージを 64 ビット モードで実行するには、SAP GUI ファイルの 64 ビット バージョンである librfc32.dll を、Windows フォルダー内の **system32** フォルダーにコピーします (通常は、このファイルの場所は、 **C:\Windows\system32**です)。  
  
-   任意の 64 ビット Windows オペレーティング システムで、パッケージを 32 ビット モードで実行するには、SAP GUI ファイルである librfc32.dll を、Windows フォルダー内の **SysWow64** フォルダーにコピーします (通常は、このフォルダーの場所は、 **C:\Windows\SysWow64**です)。  
  
  
