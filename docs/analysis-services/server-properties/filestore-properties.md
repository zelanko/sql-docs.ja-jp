---
title: "Filestore プロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Income property
- InitialBonus property
- PercentScanPerPrice property
- FileStore properties
- BackgroundTrimCost property
- Tax property
- PerformanceTrace property
- MinimumBalance property
- UnbufferedThreshold property
- BackgroundTrimAmount property
- MaximumBalance property
- MemoryLimitMin property
- MemoryLimit property
ms.assetid: 580cf0aa-7425-4d48-aa8d-128f5b488fcd
caps.latest.revision: "19"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 24a18751c7686de2d3d3731806374fe7a6db2080
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="filestore-properties"></a>FileStore プロパティ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ファイルストア サーバー プロパティは、次の表に一覧表示をサポートしています。 これらはすべて詳細プロパティなので、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。 その他のサーバー プロパティとその設定方法の詳細については、「 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)」を参照してください。  
  
 **適用対象:** 多次元サーバー モードおよびテーブル サーバー モード  
  
## <a name="properties"></a>[プロパティ]  
 **MemoryLimit**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MemoryLimitMin**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **PercentScanPerPrice**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **PerformanceTrace**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **RandomFileAccessMode**  
 データベース ファイルとキャッシュ ファイルに、ランダム ファイル アクセス モードでアクセスするかどうかを示すブール型プロパティです。 このプロパティは既定で無効になっています。 既定では、Analysis Services は、読み取りアクセス用のパーティション データ ファイルを開くときにランダム ファイル アクセス フラグを設定しません。  
  
 特に、大容量メモリ リソースと複数の NUMA ノードがあるハイエンド システムでは、ランダム ファイル アクセスを使用すると便利な場合があります。 ランダム アクセス モードでは、Windows はディスクからシステム ファイル キャッシュにデータを読み込むページ マッピング操作をバイパスするため、キャッシュの競合が減少します。  
  
 このプロパティを変更したためにクエリのパフォーマンスが向上したかどうかを判断するには、比較テストを実行する必要があります。 キャッシュの消去、一般的な間違いの回避など、比較テストの実行に関するベスト プラクティスについては、「 [SQL Server 2008 R2 Analysis Services 操作ガイド](http://go.microsoft.com/fwlink/?LinkID=225539)」を参照してください。 このプロパティを使用する際に発生するトレードオフの詳細については、 [http://support.microsoft.com/kb/2549369](http://support.microsoft.com/kb/2549369)をご覧ください。  
  
 Management Studio でこのプロパティを表示または変更するには、サーバーのプロパティ ページで詳細プロパティの一覧を有効にします。 また、msmdsrv.ini ファイルで変更することもできます。 このプロパティを設定したら、サーバーを再起動することをお勧めします。再起動しない場合、既に開いているファイルへのアクセスは、引き続き以前のモードで行われます。  
  
 **UnbufferedThreshold**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
## <a name="memory-model-category"></a>メモリ モデル カテゴリ  
 **MemoryModel\Tax**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MemoryModel\Income**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MemoryModel\MaximumBalance**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MemoryModel\MinimumBalance**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MemoryModel\InitialBonus**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Analysis Services インスタンスのサーバー モードの決定](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
