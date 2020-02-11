---
title: Integration Services サービスによってログに記録されるイベント | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- service [Integration Services], events
- events [Integration Services], service
- Integration Services service, events
ms.assetid: d4122dcf-f16f-47a0-93a2-ffa3d0d4f9cf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: dedffe0f30c62399e4d694f7ee1bf5247222e87d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62889276"
---
# <a name="events-logged-by-the-integration-services-service"></a>Integration Services サービスによってログに記録されるイベント
  
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスは、各種のメッセージを Windows アプリケーション イベント ログに記録します。 これらのメッセージは、サービスの起動時、サービスの停止時、および特定の問題の発生時にログに記録されます。  
  
 このトピックでは、アプリケーション イベント ログに記録される一般的なイベント メッセージについて説明します。 
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスは、SQLISService のイベント ソースを使用してこのトピックで説明されているすべてのメッセージをログに記録します。  
  
 
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスの概要については、「[Integration Services サービス &#40;SSIS サービス&#41;](integration-services-service-ssis-service.md)」を参照してください。  
  
## <a name="messages-about-the-status-of-the-service"></a>サービスの状態に関するメッセージ  
 インストールで [ [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ] を選択すると、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスがインストールおよび起動され、スタートアップの種類が自動に設定されます。  
  
|イベント ID|シンボル名|Text|メモ|  
|--------------|-------------------|----------|-----------|  
|256|DTS_MSG_SERVER_STARTING|サービス[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)]を開始しています。|サービスが開始されようとしています。|  
|257|DTS_MSG_SERVER_STARTED|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssIS](../../includes/ssis-md.md)]サービスが開始されました。|サービスが開始されました。|  
|260|DTS_MSG_SERVER_START_FAILED|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssIS](../../includes/ssis-md.md)]サービスを開始できませんでした。% n エラー: %1|サービスを開始できませんでした。 開始できないのは、インストールが破損したか、サービス アカウントが適切でないことが原因である可能性があります。|  
|258|DTS_MSG_SERVER_STOPPING|サービス[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)]を停止しています。% n% n 実行中のすべてのパッケージを終了時に停止します: %1|サービスを停止しています。また、パッケージを停止するようにサービスを構成している場合は、実行中のパッケージもサービスによってすべて停止されます。 構成ファイルで true 値または false 値を設定して、サービスの停止時に実行中のパッケージを停止するかどうかを指定できます。 このイベントのメッセージには、この設定値が含まれています。|  
|259|DTS_MSG_SERVER_STOPPED|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssIS](../../includes/ssis-md.md)]サービスが停止しました。% n サーバーのバージョン %1|サービスが停止しました。|  
  
## <a name="messages-about-the-configuration-file"></a>構成ファイルに関するメッセージ  
 
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスの設定は、変更可能な XML ファイルに格納されています。 詳細については、「 [Integration Services サービスの構成 (SSIS サービス)](../configuring-the-integration-services-service-ssis-service.md)との互換性を維持するために、このサービスをサポートしています。  
  
|イベント ID|シンボル名|Text|メモ|  
|--------------|-------------------|----------|-----------|  
|274|DTS_MSG_SERVER_MISSING_CONFIG_REG|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssIS](../../includes/ssis-md.md)]サービス:% n 構成ファイルを指定するレジストリ設定が存在しません。 %n既定の構成ファイルを読み込もうとしています。|構成ファイルのパスを含むレジストリ エントリが存在しないか、空です。|  
|272|DTS_MSG_SERVER_MISSING_CONFIG|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssIS](../../includes/ssis-md.md)]サービス構成ファイルが存在しません。% n 既定の設定を使用して読み込んでいます。|指定した場所に構成ファイル自体が存在しません。|  
|273|DTS_MSG_SERVER_BAD_CONFIG|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssIS](../../includes/ssis-md.md)]サービス構成ファイルが正しくありません。% n 構成ファイルを読み取っています: %1% n% n 既定の設定を使用してサーバーを読み込んでいます。|構成ファイルを読み取ることができないか、無効です。 このエラーは、ファイル内の XML 構文エラーによって発生する可能性があります。|  
  
## <a name="other-messages"></a>その他のメッセージ  
  
|イベント ID|シンボル名|Text|メモ|  
|--------------|-------------------|----------|-----------|  
|336|DTS_MSG_SERVER_STOPPING_PACKAGE|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssIS](../../includes/ssis-md.md)]サービス: 実行中のパッケージを停止しています。% n パッケージインスタンス ID: %1% n パッケージ ID: %2% n パッケージ名: %3% n パッケージの説明: %4% n パッケージ|実行中のパッケージをサービスが停止しようとしています。 実行中のパッケージは、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で監視および停止できます。 
  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] でパッケージを管理する方法については、「[パッケージの管理 &#40;SSIS サービス&#41;](package-management-ssis-service.md)」を参照してください。|  
  
## <a name="related-tasks"></a>Related Tasks  
 ログ エントリを表示する方法については、「 [[ログ イベント] ウィンドウでログ エントリを表示する](../view-log-entries-in-the-log-events-window.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Integration Services パッケージによってログに記録されるイベント](../performance/events-logged-by-an-integration-services-package.md)  
  
  
