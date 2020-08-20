---
description: DQS クレンジング接続マネージャー
title: DQS クレンジング接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: faa1eedd-db14-41e5-8e58-8f0f6f561e42
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 051a2c558675d4d80b0b414668fcd3c4cb824478
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88477947"
---
# <a name="dqs-cleansing-connection-manager"></a>DQS クレンジング接続マネージャー

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  DQS クレンジング接続マネージャーを使用すると、パッケージから [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] サーバーに接続できます。 DQS クレンジング変換では、DQS クレンジング接続マネージャーを使用します。  
  
 Data Quality Services について詳しくは、「 [Data Quality Services の概念](../../data-quality-services/data-quality-services-concepts.md)」をご覧ください。  
  
> [!IMPORTANT]  
>  DQS クレンジング接続マネージャーでは、Windows 認証のみがサポートされています。  
  
## <a name="related-tasks"></a>Related Tasks  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティについて詳しくは、「 [[DQS クレンジング変換エディター] ダイアログ ボックス](../../integration-services/data-flow/transformations/dqs-cleansing-transformation-editor-dialog-box.md)」をご覧ください。  
  
 プログラムによる接続マネージャーの構成については、開発者ガイドの <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> クラスのドキュメントをご覧ください。  
  
  
