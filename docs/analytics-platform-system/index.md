---
title: Analytics Platform System のドキュメント | Microsoft Docs
description: データ ウェアハウジングとビッグ データの分析用に設計されたデータ プラットフォームである Microsoft Analytics Platform System (APS) では、データの密な統合、クエリの高速処理、非常に拡張性の高い記憶域が提供され、エンド ツー エンドのビジネス インテリジェンス ソリューションを簡単にメンテナンスできます。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 62fefedaa417e73820a7e14df9bf90f6215b9161
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51702450"
---
# <a name="microsoft-analytics-platform-system"></a>Microsoft Analytics Platform System  
データ ウェアハウジングとビッグ データの分析用に設計されたデータ プラットフォームである Microsoft Analytics Platform System (APS) では、データの密な統合、クエリの高速処理、非常に拡張性の高い記憶域が提供され、エンド ツー エンドのビジネス インテリジェンス ソリューションを簡単にメンテナンスできます。  
  
![アプライアンスのアーキテクチャ](media/architecture-high-level.png "アプライアンスのアーキテクチャ")  
  
Analytics Platform System は、超並列処理 (MPP) データ ウェアハウスを実行するソフトウェアである SQL Server 並列データ ウェアハウス (PDW) をホストしています。  
  
PolyBase テクノロジは、Windows Server の Hortonworks、Linux の Hortonworks、Linux の Cloudera、HDInsight の Microsoft Azure BLOB Storage など、複数のソースから得られるリレーショナル PDW データと Hadoop データを結合します。 データを高度に統合できるこれらの機能に加え、ビジネス インテリジェンス ツールとの密な統合により、ビジネスの意思決定者が、よりよい洞察を備えたビジネス上の意思決定を下せるようにする分析を Analytics Platform System が返すことができます。  
  
Analytics Platform System は、ハードウェアとソフトウェアが事前にインストールされ、複数のワークロードを実行できるように構成されたアプライアンスとしてデータ センターに出荷されます。 Analytics Platform System を購入する場合、ビジネス要件に応じて PDW 用のコンピューティング ノードを購入します。  
  
Analytics Platform System は高速で拡張性があるだけではなく、高い冗長性と可用性を備えて設計されているため、ビジネス上の重要なほとんどのデータに対して信頼できる、安定したプラットフォームです。 Analytics Platform System は覚えやすく管理しやすいようにわかりやすく設計されています。 PDW は、Hadoop データを分析するための PolyBase テクノロジと、ビジネス インテリジェンス ツールとの密な統合により、エンド ツー エンドのソリューションを構築するための包括的なプラットフォームになっています。  
  
  
## <a name="parallel-data-warehouse-software-designed-for-massively-parallel-processing"></a>超並列処理用に設計された並列データ ウェアハウス ソフトウェア
  
PDW は、エンド ツー エンドのビジネス インテリジェンス ソリューションのリレーショナル データ ウェアハウス コンポーネントとして使用できます。 PDW の超並列処理 (MPP) 設計により、クエリは、対称型マルチプロセッシング (SMP) データベース管理システム上に構築された従来のデータ ウェアハウスよりも 50 倍も高速に完了します。  
  
> [!NOTE]  
> 50 倍とは、数時間ではなく数分に、または数分ではなく数秒でクエリが完了することを意味します。 この革新的なパフォーマンスにより、ビジネス アナリストはより高速に広範な結果を生成したり、より簡単にアドホック クエリを実行したり、詳細にドリル ダウンできます。 その結果、企業はよりよい決定を今までよりも迅速に行えるようになります。  
  
PDW では、画期的なパフォーマンスを得られるだけではなく、次も容易にします。  
  
-   既存のシステムに “スケール ユニット” を追加することにより、1 つのアプライアンスのデータ ウェアハウスのデータ量を、数テラバイトから 6 ペタバイトを超えるものに増やすことができます。  
  
-   高い冗長性と可用性が組み込まれているため、データが必要なときに、すぐそこにあると信頼できます。  
  
-   データの読み込みや統合に関する現代の課題を解決できます。  
  
-   PDW の高度に並列化された PolyBase テクノロジを使用することにより、Hadoop データとリレーショナル データを統合して高速に分析することができます。  
  
-   ビジネス インテリジェンス ツールを使用して、包括的なエンド ツー エンド ソリューションを構築できます。  

## <a name="next-steps"></a>次の手順

PDW の利点の詳細については、MSDN でホワイトペーパー「[A Breakthrough Platform for Next-Generation Data Warehousing and Big Data Solutions](https://msdn.microsoft.com/library/dn520808.aspx)」 (次世代のデータ ウェアハウジング ソリューションとビッグ データ ソリューションのための画期的なプラットフォーム) を参照してください。  
  

