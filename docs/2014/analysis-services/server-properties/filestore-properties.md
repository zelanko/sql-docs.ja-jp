---
title: Filestore Properties |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
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
author: minewiskan
ms.author: owend
ms.openlocfilehash: db238092ac4c77e94961152808c7a7b6e76e9790
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84940693"
---
# <a name="filestore-properties"></a>FileStore プロパティ
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、次の表に示すファイルストア サーバー プロパティがサポートされています。 これらはすべて詳細プロパティなので、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。 その他のサーバー プロパティとその設定方法の詳細については、「 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)」を参照してください。  
  
 **適用対象:** 多次元サーバー モードおよびテーブル サーバー モード  
  
## <a name="properties"></a>プロパティ  
 `MemoryLimit`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 `MemoryLimitMin`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 `PercentScanPerPrice`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 `PerformanceTrace`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 `RandomFileAccessMode`  
 データベース ファイルとキャッシュ ファイルに、ランダム ファイル アクセス モードでアクセスするかどうかを示すブール型プロパティです。 このプロパティは既定で無効になっています。 既定では、Analysis Services は、読み取りアクセス用のパーティション データ ファイルを開くときにランダム ファイル アクセス フラグを設定しません。  
  
 特に、大容量メモリ リソースと複数の NUMA ノードがあるハイエンド システムでは、ランダム ファイル アクセスを使用すると便利な場合があります。 ランダム アクセス モードでは、Windows はディスクからシステム ファイル キャッシュにデータを読み込むページ マッピング操作をバイパスするため、キャッシュの競合が減少します。  
  
 このプロパティを変更したためにクエリのパフォーマンスが向上したかどうかを判断するには、比較テストを実行する必要があります。 キャッシュの消去、一般的な間違いの回避など、比較テストの実行に関するベスト プラクティスについては、「 [SQL Server 2008 R2 Analysis Services 操作ガイド](https://go.microsoft.com/fwlink/?LinkID=225539)」を参照してください。 このプロパティを使用する場合のトレードオフの詳細については、「」を参照してください [https://support.microsoft.com/kb/2549369](https://support.microsoft.com/kb/2549369) 。  
  
 Management Studio でこのプロパティを表示または変更するには、サーバーのプロパティ ページで詳細プロパティの一覧を有効にします。 また、msmdsrv.ini ファイルで変更することもできます。 このプロパティを設定したら、サーバーを再起動することをお勧めします。再起動しない場合、既に開いているファイルへのアクセスは、引き続き以前のモードで行われます。  
  
 `UnbufferedThreshold`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
## <a name="memory-model-category"></a>メモリ モデル カテゴリ  
 `MemoryModel\Tax`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 `MemoryModel\Income`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 `MemoryModel\MaximumBalance`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 `MemoryModel\MinimumBalance`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 `MemoryModel\InitialBonus`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services でのサーバープロパティの構成](server-properties-in-analysis-services.md)   
 [Analysis Services インスタンスのサーバー モードの決定](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
