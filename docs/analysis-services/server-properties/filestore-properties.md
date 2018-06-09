---
title: Filestore プロパティ |Microsoft ドキュメント
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3a5bf8e90352218b222bbd6a58ad876ca0e1364b
ms.sourcegitcommit: 6e55a0a7b7eb6d455006916bc63f93ed2218eae1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2018
ms.locfileid: "35239042"
---
# <a name="filestore-properties"></a>Filestore プロパティ
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サポートしている、`filestore`サーバー プロパティは、次の表に一覧表示します。 これらはすべて詳細プロパティなので、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。 その他のサーバー プロパティとその設定方法の詳細については、「 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)」を参照してください。  
  
 **適用対象:** 多次元サーバー モードおよびテーブル サーバー モード  
  
## <a name="properties"></a>プロパティ  
 **MemoryLimit**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MemoryLimitMin**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **PercentScanPerPrice**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **PerformanceTrace**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **RandomFileAccessMode**  
 データベース ファイルとキャッシュ ファイルに、ランダム ファイル アクセス モードでアクセスするかどうかを示すブール型プロパティです。 このプロパティは既定で無効になっています。 既定では、サーバーはランダム ファイル アクセス フラグを設定できませんへの読み取りアクセス用のパーティション データ ファイルを開くときにします。  
  
 特に、大容量メモリ リソースと複数の NUMA ノードがあるハイエンド システムでは、ランダム ファイル アクセスを使用すると便利な場合があります。 ランダム アクセス モードでは、Windows は、データをディスクからシステム ファイル キャッシュに読み込むページ マッピング操作に、キャッシュの競合を低くをスキップします。  
  
 このプロパティを変更したためにクエリのパフォーマンスが向上したかどうかを判断するには、比較テストを実行する必要があります。 キャッシュの消去、一般的な間違いの回避など、比較テストの実行に関するベスト プラクティスについては、「 [SQL Server 2008 R2 Analysis Services 操作ガイド](http://go.microsoft.com/fwlink/?LinkID=225539)」を参照してください。 このプロパティを使って、トレードオフの詳細については、次を参照してください。 [ http://support.microsoft.com/kb/2549369](http://support.microsoft.com/kb/2549369)です。  
  
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
  
  
