---
title: Microsoft Connector for 1.1 SAP BW のインストール |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a4362773ab6e0ec0252062d1695a921e7054226
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85424749"
---
# <a name="installing-the-microsoft-connector-for-11-sap-bw"></a>Microsoft Connector 1.1 for SAP BW のインストール
  [!INCLUDE[msCoName](../includes/msconame-md.md)]SAP BW とそのドキュメントのコネクタ1.1 をインストールするには、SQL Server Feature Pack Web ページから Windows インストーラーパッケージをダウンロードして実行します。  
  
> [!IMPORTANT]  
>  Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。 SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。  
  
> [!IMPORTANT]  
>  SAP Netweaver BW からデータを抽出するには、追加の SAP のライセンスが必要です。 これらの要件を確認するには、SAP にお問い合わせください。  
  
## <a name="required-sap-files"></a>必要な SAP のファイル  
 SAP BW にコネクタ1.1 を使用するには [!INCLUDE[msCoName](../includes/msconame-md.md)] 、Sap フロントエンドソフトウェア (SAP GUI) をローカルコンピューターにインストールする必要はありません。  
  
 ただし、SAP の .NET コネクタ ファイルである librfc32.dll を、Windows フォルダー内の system サブフォルダーにコピーする必要があります (通常は、このフォルダーの場所は、 **C:\Windows\system32**です)。  
  
## <a name="considerations-for-64-bit-computers"></a>64 ビット コンピューターに関する注意事項  
 [!INCLUDE[msCoName](../includes/msconame-md.md)]コネクタ 1.1 for SAP BW は、Windows の64ビットバージョンを完全にサポートして [!INCLUDE[msCoName](../includes/msconame-md.md)] います。 64ビットコンピューターの場合、 [!INCLUDE[msCoName](../includes/msconame-md.md)] SAP BW のコネクタ1.1 には、次の追加要件があります。  
  
-   任意の 64 ビット Windows オペレーティング システムで、パッケージを 64 ビット モードで実行するには、SAP GUI ファイルの 64 ビット バージョンである librfc32.dll を、Windows フォルダー内の **system32** フォルダーにコピーします (通常は、このファイルの場所は、 **C:\Windows\system32**です)。  
  
-   任意の 64 ビット Windows オペレーティング システムで、パッケージを 32 ビット モードで実行するには、SAP GUI ファイルである librfc32.dll を、Windows フォルダー内の **SysWow64** フォルダーにコピーします (通常は、このフォルダーの場所は、 **C:\Windows\SysWow64**です)。  
  
  
