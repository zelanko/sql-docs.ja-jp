---
title: メモリのプロパティ |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- LowMemoryLimit property
- MinimumAllocatedMemory property
- MidMemoryPrice property
- MemoryHeapType property
- memory [Analysis Services]
- DefaultPagesCountToReuse property
- TotalMemoryLimit property
- SessionMemoryLimit property
- VirtualMemoryLimit property
- WaitCountIfHighMemory property
- HighMemoryPrice property
- HeapTypeForObjects property
ms.assetid: 085f5195-7b2c-411a-9813-0ff5c6066d13
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c80e57803c1635cf6688ac8d8a562aa7e40f8818
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076063"
---
# <a name="memory-properties"></a>メモリのプロパティ
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、次の表に示すサーバー メモリ プロパティがサポートされています。 これらのプロパティの設定方法については、「 [SQL Server 2008 R2 Analysis Services 操作ガイド](http://go.microsoft.com/fwlink/?LinkID=225539)」を参照してください。  
  
 1 ～ 100 の値は、 **[物理メモリの合計]** または **[仮想アドレス領域]** のどちらか少ない方に対する割合を示します。 100 を超える値はメモリ制限を示します (単位: バイト)。  
  
 **適用対象:** 特に記載のない限り、多次元サーバー モードおよびテーブル サーバー モードが対象となります。  
  
## <a name="properties"></a>[プロパティ]  
 `LowMemoryLimit`  
 サーバーがメモリ不足になる時点を定義する、符号付き 64 ビット倍精度浮動小数点数のプロパティ。合計物理メモリの比率として表されます。 この制限に達すると、インスタンスは、期限切れのセッションを終了したり、使用されていない計算をアンロードしたりすることによって、徐々にキャッシュ内のメモリを解放し始めます。 この制限を下回っている間は、メモリは解放されません。 既定値は 65 です。これは、物理メモリまたは仮想アドレス空間の 65% (どちらか少ない方) を超えたらメモリ不足とすることを示します。  
  
 `TotalMemoryLimit`  
 サーバーが、より積極的にメモリを解放し始めるしきい値を定義します。 既定値は、物理メモリまたは仮想アドレス空間の 80% です (どちらか少ない方)。  
  
 `TotalMemoryLimit` は常に、`HardMemoryLimit` より小さくする必要があります。  
  
 `HardMemoryLimit`  
 インスタンスが、メモリ使用量を減らすために、アクティブなユーザー セッションを積極的に終了し始めるメモリのしきい値を指定します。 終了されたすべてのセッションには、メモリ不足によって使用中止となった旨のエラーが送信されます。 既定値はゼロ (0) の意味、`HardMemoryLimit`間の値に設定されます`TotalMemoryLimit`とシステム プロセス、し、仮想アドレスの仮想アドレス空間よりも大きい場合は、システムの物理メモリの合計物理メモリ使用する領域を代わりに計算する`HardMemoryLimit`です。  
  
 `VirtualMemoryLimit`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 `VertiPaqPagingPolicy`  
 サーバーのメモリが不足したときのページングの動作を指定します。 有効な値は次のとおりです。  
  
 0 (**0**) ページングを無効にします。 メモリが足りなくなると、メモリ不足エラーが発生し、処理は失敗します。 ページングを無効にする場合は、サービス アカウントに Windows 特権を付与する必要があります。 手順については、「[サービス アカウントの構成 (Analysis Services)](../instances/configure-service-accounts-analysis-services.md)」を参照してください。  
  
 **1** が既定値です。 このプロパティを指定した場合、オペレーティング システムのページング ファイル (pagefile.sys) を使用してディスクへのページングが行われます。  
  
 ときに`VertiPaqPagingPolicy`設定は 1、処理はサーバーが指定したメソッドを使用してディスクへのページングを試行するために、メモリ制約によって失敗する可能性は低くします。 `VertiPaqPagingPolicy` プロパティを設定しても、メモリ エラーが発生しないことが保証されるわけではありません。 以下の状況では、メモリ不足エラーが発生する可能性があります。  
  
-   すべての辞書のための十分なメモリがない。 処理中に、Analysis Services は、メモリ内の各列の辞書をロックし、それらすべてのする指定された値を超えることはできません`VertiPaqMemoryLimit`です。  
  
-   処理に対応するための十分な仮想アドレス空間がない。  
  
 繰り返し発生するメモリ不足エラーを解決するには、処理を要するデータの量を減らすようにモデルを設計し直すか、コンピューターに物理メモリを追加します。  
  
 テーブル サーバー モードにのみ適用されます。  
  
 `VertiPaqMemoryLimit`  
 ディスクへのページングを許可した場合に、ページングが開始されるメモリ消費レベル (メモリの合計に対する割合) をこのプロパティで指定します。 既定値は 60 です。 メモリ消費量が 60% 未満の場合、ディスクへのページングは実行されません。  
  
 このプロパティによって異なります、 `VertiPaqPagingPolicyProperty`、ページングを有効にするために 1 に設定する必要があります。  
  
 テーブル サーバー モードにのみ適用されます。  
  
 `HighMemoryPrice`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 `MemoryHeapType`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 多次元サーバー モードにのみ適用されます。  
  
 `HeapTypeForObjects`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 多次元サーバー モードにのみ適用されます。  
  
 `DefaultPagesCountToReuse`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 `HandleIA64AlignmentFaults`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 `MidMemoryPrice`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 `MinimumAllocatedMemory`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 `PreAllocate`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 `SessionMemoryLimit`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 `WaitCountIfHighMemory`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
## <a name="see-also"></a>参照  
 [Analysis services サーバーのプロパティを構成します。](server-properties-in-analysis-services.md)   
 [Analysis Services インスタンスのサーバー モードの決定](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  