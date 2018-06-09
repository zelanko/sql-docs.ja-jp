---
title: メモリのプロパティ |Microsoft ドキュメント
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 57a40130b9cf8ddf2b2f9d3c43d464436a0f4730
ms.sourcegitcommit: 6e55a0a7b7eb6d455006916bc63f93ed2218eae1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2018
ms.locfileid: "35239122"
---
# <a name="memory-properties"></a>メモリのプロパティ
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 要求がすぐに処理できるように、適度な量の起動時にメモリに事前に割り当てます。 追加のメモリがクエリに割り当てられ、処理のワークロードが増大します。 
  
  構成設定を指定すると、メモリが解放されるしきい値を制御することができます。 たとえば、 **HardMemoryLimit** 設定では、メモリ不足の条件を自分で指定します (既定では、このしきい値は有効ではありません)。ここでは、新しい要求は追加のリソースが有効になるまで完全に拒否されます。

エディションで使用される Analysis Services インスタンスあたり最大メモリの詳細については、次を参照してください。[エディションと SQL Server のサポートされる機能](../../sql-server/editions-and-components-of-sql-server-2017.md#Cross-BoxScaleLimits)します。
  
 次の設定は、特に明記しない限り、両方のテーブルと多次元サーバー モードに適用されます。  
 
## <a name="default-memory-configuration"></a>既定のメモリ構成

既定の構成は、各 Analysis Services インスタンスは、場合でも、インスタンスがアイドル状態に起動時、少量の RAM (40 MB ~ 50 MB) を割り当てます。 

構成設定はインスタンスごとであることに注意してください。 同じハードウェアのテーブルと多次元インスタンスなど、Analysis Services の複数のインスタンスを実行している場合、他のインスタンスとは関係なく、各インスタンスで固有のメモリを割り当てます。

次の表では、(リファレンス セクションの詳細情報と共に) 一般的に使用されるメモリの設定について簡単に説明します。 これらの Analysis Services が同じサーバー上の他のアプリケーションとメモリの競合する場合にのみ設定を構成する必要があります。

設定 | 説明
--------|------------
LowMemoryLimit | 多次元インスタンスで、最初にサーバーが、使用されるオブジェクトと関係なく割り当てられたメモリを解放し始める下限のしきい値。
VertiPaqMemoryLimit | テーブルインスタンスで、最初にサーバーが、使用されるオブジェクトと関係なく割り当てられたメモリを解放し始める下限のしきい値。
TotalMemoryLimit | 実行中の要求および新しい優先度の高い要求に対してスペースを作るために、Analysis Services が積極的にさらにメモリを解放し始める上限のしきい値。 
HardMemoryLimit | Analysis Services がメモリ不足のために、完全に要求を拒否し始める別のしきい値。 
 
## <a name="property-reference"></a>プロパティ リファレンス

次のプロパティは、それ以外に指定されない限り、テーブルと多次元の両方のモードに適用されます。

 1 ～ 100 の値は、 **[物理メモリの合計]** または **[仮想アドレス領域]** のどちらか少ない方に対する割合を示します。 100 を超える値はメモリ制限を示します (単位: バイト)。
  
 **LowMemoryLimit**  
 符号付き 64 ビット倍精度浮動小数点数のプロパティを Analysis Services が、使用頻度の低いキャッシュなどの優先度の低いオブジェクトのメモリの解放を開始する最初のしきい値を定義します。 メモリを割り当てると、サーバーはこの制限より下のメモリを解放することはありません。 既定値は 65 です。これは、物理メモリまたは仮想アドレス空間の 65% (どちらか少ない方) を超えたらメモリ不足とすることを示します。  
  
 **TotalMemoryLimit**  
 他の要求用にスペースを作るために、サーバーがメモリの割り当てを解除し始めるしきい値を定義します。 この制限に達すると、インスタンスは、期限切れのセッションを終了したり、使用されていない計算をアンロードしたりすることによって、徐々にキャッシュ内のメモリを解放し始めます。 既定値は、物理メモリまたは仮想アドレス空間の 80% です (どちらか少ない方)。 **TotalMemoryLimit**常にする必要がありますより小さい**HardMemoryLimit**  
  
 **HardMemoryLimit**  
 インスタンスが、メモリ使用量を減らすために、アクティブなユーザー セッションを積極的に終了し始めるメモリのしきい値を指定します。 終了されたすべてのセッションには、メモリ不足で取り消されるについて、エラーが発生します。 既定値 (0) は、 **HardMemoryLimit** が **TotalMemoryLimit** とシステムの物理メモリ合計の間の値に設定されることを意味します。システムの物理メモリがプロセスの仮想アドレス領域を超える場合は、 **HardMemoryLimit**を計算せずに、仮想アドレス空間が使用されます。  

**QueryMemoryLimit**   
Azure Analysis Services の場合のみです。 メモリの量は、クエリ中に一時的な結果で使用できますを制御する高度なプロパティです。 DAX メジャーおよびクエリにのみ適用されます。 多次元モードのサーバーに対して MDX クエリでは、この制限は使用しません。 クエリで使用される一般的なメモリ割り当ては考慮しません。 比率で指定します。 制限が指定されていない 0 の場合の既定値。

 **VirtualMemoryLimit**  
  詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **VertiPaqPagingPolicy**  
  テーブル インスタンスのみの場合、サーバーのメモリが不足したときのページングの動作を指定します。 有効な値は次のとおりです。  
  
  

設定  |説明  
---------|---------
**0**     |  ページングを無効にします。 メモリが足りなくなると、メモリ不足エラーが発生し、処理は失敗します。 ページングを無効にする場合は、サービス アカウントに Windows 特権を付与する必要があります。 手順については、「[サービス アカウントの構成 (Analysis Services)](../../analysis-services/instances/configure-service-accounts-analysis-services.md)」を参照してください。 
**1**     |  (既定値) このプロパティを指定した場合、オペレーティング システムのページング ファイル (pagefile.sys) を使用してディスクへのページングが行われます。   
  
1 に設定された場合、指定された方法を使用してサーバーがディスクへのページングを試行するので、メモリ制約によって処理が失敗する可能性は低くなります。 **VertiPaqPagingPolicy** プロパティを設定しても、メモリ エラーが発生しないことが保証されるわけではありません。 以下の状況では、メモリ不足エラーが発生する可能性があります。  
  
-   すべての辞書のための十分なメモリがない。 処理中に、サーバーは、メモリ内の各列の辞書をロックし、それらすべてのする指定された値を超えることはできません**VertiPaqMemoryLimit**です。  
  
-   処理に対応するための十分な仮想アドレス空間がない。  
  
 繰り返し発生するメモリ不足エラーを解決するには、処理を要するデータの量を減らすようにモデルを設計し直すか、コンピューターに物理メモリを追加します。  
  
 **VertiPaqMemoryLimit**  
 テーブル インスタンスのみの場合、ディスクへのページングを許可していれば、ページングが開始されるメモリ消費レベル (メモリの合計に対する割合) をこのプロパティで指定します。 既定値は 60 です。 メモリ消費量が 60% 未満の場合、ディスクへのページングは実行されません。 このプロパティは、 **VertiPaqPagingPolicyProperty**に依存します (ページングを有効にするには 1 に設定する必要があります)。  
  
 **HighMemoryPrice**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MemoryHeapType**  
  詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。 SQL Server 2016 SP1 とそれ以降の Analysis Services で有効な値は次のとおりです。
  
  設定 | 説明
--------|------------
**-1** | (既定値) 自動。 エンジンがどれを使用するかを決定します。
**1** | Analysis Services ヒープ。
**2** | Windows LFH。
**5** | ハイブリッド アロケーター。 このアロケーターを使用の Windows LFH \<= 16 KB の割り当てと AS のヒープ > 16 KB の割り当て。 
**6** | Intel TBB アロケーター。 SQL Server 2016 SP1 (およびそれ以降) の Analysis Services で使用できます。
  
  
 **HeapTypeForObjects**  
  詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。 有効な値は次のとおりです。
  
   設定 | 説明
--------|------------
**0** | Windows LFH ヒープ。
**1** | Analysis Services スロット アロケーター。
**3** | 各オブジェクトには独自の Analysis Services ヒープがあります。

 
 **DefaultPagesCountToReuse**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **HandleIA64AlignmentFaults**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MidMemoryPrice**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MinimumAllocatedMemory**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **PreAllocate**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **SessionMemoryLimit**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **WaitCountIfHighMemory**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Analysis Services インスタンスのサーバー モードの決定](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
