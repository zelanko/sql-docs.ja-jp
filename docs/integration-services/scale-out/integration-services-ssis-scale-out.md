---
title: "SQL Server Integration Services (SSIS) のスケール アウト |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dcfbd1c5-c001-4fb7-b9ae-916e49ab6a96
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ce7fb96901e8af4da74392fe0a0a85c6e2ec05a4
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="integration-services-ssis-scale-out"></a>Integration Services (SSIS) Scale Out
[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out では、実行を複数のコンピューターに分散することで、パッケージを高いパフォーマンスで実行できます。 SQL Server Management Studio での複数のパッケージ実行の要求を送信することができます。 これらのパッケージは、Scale Out モードで並列実行されます。  

[!INCLUDE[ssIS_md](../../includes/ssis-md.md)]スケール アウトから成る、[!INCLUDE[ssIS_md](../../includes/ssis-md.md)]スケール アウト マスターと 1 つまたは複数[!INCLUDE[ssIS_md](../../includes/ssis-md.md)]スケール アウト ワーカーです。 Scale Out Master は、Scale Out の管理を担当し、ユーザーからパッケージの実行要求を受け取ります。 Scale Out Worker は、Scale Out Master から実行作業をプルし、パッケージの実行作業を実行します。 詳細については、「[Scale Out Master](integration-services-ssis-scale-out-master.md)」と「[Scale Out Worker](integration-services-ssis-scale-out-worker.md)」を参照してください。

[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]ここで、スケール アウト マスターと、スケール アウト ワーカーが設定されてコンピューターに並列で、1 台のコンピューターでは、スケール アウトを構成できます。 Scale Out は、Scale Out Worker がそれぞれ別のコンピューターに配置された複数のコンピューターで実行することも可能です。
- [チュートリアル: Integration Services Scale Out をセットアップする](walkthrough-set-up-integration-services-scale-out.md)

Scale Out では、SSISDB カタログの複数のパッケージを並列で実行できます。 詳細については、[「Integration Services (SSIS) Scale Out でパッケージを実行する」](run-packages-in-integration-services-ssis-scale-out.md)をご覧ください。

