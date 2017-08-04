---
title: "Linux 上の SQL Server の共有ディスク クラスターの構成 |Microsoft ドキュメント"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 92b4cb2500d4fd8a1643488593c40e97b1ff6454
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---

# <a name="shared-disk-cluster-for-sql-server-on-linux"></a>Linux 上の SQL Server の共有ディスク クラスター

別のノードからフェールオーバーへの SQL Server インスタンスを許可する Linux では、共有記憶域の高可用性クラスターを構成できます。 一般的なクラスターでは、次の 2 つまたは複数のサーバーは、共有記憶域に接続されます。 サーバーは、クラスター ノードです。 フェールオーバー クラスターでは、次の 2 つまたは複数のノード間でフェールオーバーする SQL Server を許可する場合に、復旧時間を向上させるためにインスタンス レベルの保護を提供します。 構成手順は、Linux ディストリビューションとクラスタ リング ソリューションによって異なります。 次の表では、検証済みのクラスター ソリューションの特定の手順を識別します。  

|Distribution |トピック 
|----- |-----
|**HA アドオンで、Red Hat Enterprise Linux** |[構成します。](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)<br/>[動作](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**HA アドオンに SUSE Linux Enterprise Server** |[構成します。](sql-server-linux-shared-disk-cluster-sles-configure.md)

## <a name="next-steps"></a>次の手順


