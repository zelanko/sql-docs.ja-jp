---
title: 'ケーススタディ: Microsoft Dynamics ERP を使用したエンタープライズエコシステムの構築と、スケーラビリティとパフォーマンスのための SQL Server 2014 レプリケーション |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 2b0b5ab7-4e08-431a-bd59-360177c4565c
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a6cc9530b636409864e7e1b72f7417619a0fc8af
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67792469"
---
# <a name="case-study-building-an-enterprise-ecosystem-with-microsoft-dynamics-erp-and-sql-server-2014-replication-for-scalability-and-performance"></a>ケース スタディ: Microsoft Dynamics ERP と SQL Server 2014 レプリケーションを活用した、スケーラビリティとパフォーマンスの向上のためのエンタープライズ エコシステムの構築

  **概要:** このホワイトペーパーでは、次のシナリオについて説明します。  
SQL Server 2014 でトランザクションレプリケーションを使用して、Dynamics AX クライアントからのトランザクションを複数のノードに分散させる方法について説明します。 トランザクション レプリケーションでは、データが複数のノードでリアルタイムに保持されるため、データの冗長性が実現し、データの可用性が向上します。これには、パフォーマンス分析をより効率的に行うために使用できるデータも含まれます。  
Microsoft Dynamics ERP で拡張性の高いエンタープライズ エコシステムを構築するためにトランザクション レプリケーションを活用する際に関係する詳細事項を理解する方法。 AX の既定の機能をカスタマイズすることなく、高いパフォーマンスとスケーラビリティを提供します。  
  
 トランザクション レプリケーションは、高いスループットが必要とされるサーバー間のワークフローで使われるのが一般的です。 たとえば、スケーラビリティと可用性の向上、データ ウェアハウジングとレポート、複数サイトからのデータの統合、異種データの統合、バッチ処理のオフロードなどのシナリオがあります。 このホワイト ペーパーでは、Microsoft Dynamics ERP でトランザクション レプリケーションを活用する個々のシナリオと、それに関連するパターンについて説明します。 また、Enterprise Resource Planning (ERP) 固有のエンタープライズ ソリューションの構築のためにトランザクション レプリケーションを検討する際の課題とベスト プラクティスや、各段階でのパフォーマンス分析についても解説しています。  
  
 このコンテンツは、開発者、アーキテクト、データベース管理者を対象としています。 このホワイト ペーパーの読者の皆様には、SQL Server 2008、2012、2014 に関する基礎知識と、SQL Server の管理の経験があることを想定しています。  
  
 **ライター:** Prabhakaran Sethuraman (PRAB)、Microsoft  
  
 **技術レビューアー:** Prabhakaran Sethuraman (PRAB)、Microsoft、Santosh Padhy、Microsoft;Pavel Majstrov、Microsoft、Karthik Sankaranarayanan、Microsoft、Jon Acone、Microsoft;David Stahlkopf、Microsoft;Kent Oldenburger、Microsoft、Mandi Ohlinger、Microsoft;Jason Roth、Microsoft  
  
 **発行済み:** 2015年10月  
  
 **適用対象:** SQL Server 2008、SQL Server 2012、SQL Server 2014  
  
 ドキュメントを確認するには、  
        [ケーススタディ: Microsoft DYNAMICS ERP を使用したエンタープライズエコシステムの構築と、スケーラビリティとパフォーマンスのための SQL Server 2014 レプリケーション](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/A%20Case%20Study%20Using%20Replication%20to%20Build%20an%20Enterprise%20Ecosystem%20in%20Microsoft%20Dynamics%20ERP%20for%20Scalability%20and%20Performance.docx)Word 文書。  
  
  
