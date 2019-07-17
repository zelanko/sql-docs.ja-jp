---
title: Analytics Platform System のハードウェア構成 |Microsoft Docs
description: お客様のビジネス要件に従って処理およびストレージの量を適切を購入するために、スケーラブルなユニットで、Analytics Platform System (APS) アプライアンスのハードウェアが設計されています。 アプライアンスは、超える 6 ペタバイト規模のデータに数テラバイトから Parallel Data Warehouse 用のストレージをスケーリングします。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: f3e1759dcde0dd792ce5179de08e9add1ef355e8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960893"
---
# <a name="hardware-configurations---analytics-platform-system"></a>Analytics Platform System のハードウェア構成
お客様のビジネス要件に従って処理およびストレージの量を適切を購入するために、スケーラブルなユニットで、Analytics Platform System (APS) ハードウェアが設計されています。 アプライアンスの SQL Server 並列データ Wareouse (PDW) 数テラバイトからを超える 6 ペタバイト規模のデータ ストレージをスケーリングします。  
  
## <a name="contents"></a>目次  
  
-   [1 つのラック構成](#section1)  
  
-   [複数のラック構成](#section2)  

  
## <a name="section1"></a>1 つのラック構成  
アプライアンスの最初のラックには、PDW の実行に必要なコンポーネントが含まれています。 最小のアプライアンスの構成は、ラック、ネットワーク、および基本スケール単位です。 これらの図は、アプライアンスの最初のラックを構成する方法を示します。 ハードウェア ベンダーによって、最初のラックに 2 から 9 のコンピューティング ノード間でことができます。  
  
### <a name="first-rack-configurations---dell"></a>まずラック構成 - を DELL  
DELL は、アプライアンスの最小の構成では、3 つのコンピューティング ノードがあります。 最大 2 つのデータのスケール ユニットを追加するには、合計 9 個のコンピューティング ノードの最初のラックにします。  
  
![Dell の最初のラック構成](media/first-rack-configurations-dell.png "Dell 最初のラック構成")  
  
### <a name="first-rack-configurations---hpe"></a>最初の構成 - HPE をラックします。  
アプライアンスの HPE の最小の構成では、2 つのコンピューティング ノードがあります。 合計で 8 個のコンピューティング ノードの最初のラックには、最大 3 つのデータのスケール ユニットを追加できます。  
  
![HPE が最初に HPE の構成をラック](media/first-rack-configurations-hpe.png "HPE が最初に構成をラック")  
  
## <a name="section2"></a>複数のラック構成  
PDW に容量を追加するには、ネットワーク、その他のラック & ネットワーク コンポーネントに応じて、適切な機能を提供する、データのスケール ユニットを追加して、インフラストラクチャのラックことができます。 各追加のラック & ネットワーク パッシブ ホストが必要です。  
  
各ハードウェア ベンダーには、アプライアンスの容量を指定できますを追加するデータのスケール ユニットの数を指定します。 少なくとも、20% へのアップグレードのパフォーマンスを表示するには、十分なデータのスケール ユニットを追加することをお勧めします。 たとえば、1 つのデータのスケールを追加する 20 のデータのスケール ユニットに既にあるアプライアンスに単位可能性がありますごくわずかのパフォーマンスが向上。 純利益は、コストと労力の価値はないでしょう。  
  
### <a name="scale-out-example---hpe"></a>スケール アウトのサンプル - HPE  
この図は、20 のコンピューティング ノードを含む 3 つのラック HP アプライアンスを示しています。  
  
![20 のコンピューティング ノードで HPE アプライアンス](media/scale-out-hpe.png "HPE アプライアンス 20 のコンピューティング ノードの使用")  
  
### <a name="scale-out-example---dell-quanta"></a>スケール アウトの例: DELL、クォンタム  
この図は、21 のコンピューティング ノードを含む 3 つのラック DELL または Quanta アプライアンスを示しています。  
  
![21 のコンピューティング ノードの使用の Dell アプライアンス](media/scale-out-dell.png "21 のコンピューティング ノードの使用の Dell アプライアンス")  
 
