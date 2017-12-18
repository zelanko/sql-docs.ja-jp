---
title: SQL Server Integration Services (SSIS) Scale Out | Microsoft Docs
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dcfbd1c5-c001-4fb7-b9ae-916e49ab6a96
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 0277d312ce4dab14e7ba64529e3eb2251a0d2d02
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="integration-services-ssis-scale-out"></a>Integration Services (SSIS) Scale Out
[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out では、実行を複数のコンピューターに分散することで、パッケージを高いパフォーマンスで実行できます。 SQL Server Management Studio では、複数のパッケージの実行の要求を送信することができます。 これらのパッケージは、Scale Out モードで並列実行されます。  

[!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out は、1 つの [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out Master と 1 つ以上の [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out Worker で構成されます。 Scale Out Master は、Scale Out の管理を担当し、ユーザーからパッケージの実行要求を受け取ります。 Scale Out Worker は、Scale Out Master から実行作業をプルし、パッケージの実行作業を実行します。 詳細については、「[Scale Out Master](integration-services-ssis-scale-out-master.md)」と「[Scale Out Worker](integration-services-ssis-scale-out-worker.md)」を参照してください。

[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out は、Scale Out Master および Scale Out Worker が 1 台のコンピューター上に共存するようセットアップされているコンピューターで構成できます。 Scale Out は、Scale Out Worker がそれぞれ別のコンピューターに配置された複数のコンピューターで実行することも可能です。
- [チュートリアル: Integration Services Scale Out をセットアップする](walkthrough-set-up-integration-services-scale-out.md)

Scale Out では、SSISDB カタログの複数のパッケージを並列で実行できます。 詳細については、[「Integration Services (SSIS) Scale Out でパッケージを実行する」](run-packages-in-integration-services-ssis-scale-out.md)をご覧ください。
