---
title: "アーキテクチャの概要 (SQL Server R サービス) | Microsoft Docs"
ms.custom: ""
ms.date: "05/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6c4a4f66-ea3e-4a73-acf2-6c8aeafc94b0
caps.latest.revision: 9
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 9
---
# アーキテクチャの概要 (SQL Server R サービス)
このセクションのアーキテクチャの概要を説明する [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], 、セキュリティ、R のサポート コンポーネント、および SQL Server で実行されているオープン ソース R スクリプトの相互運用性に、SQL Server データベース エンジンに追加された新しいコンポーネントを含みます。


## 目標


アーキテクチャ [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] はオープン ソース R 言語をサポートするために設計されています。 R の現在のユーザーは、R コードを移植して比較的わずかな変更で T-SQL で実行できるようにする必要があります。

ただし、SQL Server の R のサービスでは、パフォーマンスの向上と高速のデータのスループットと処理を有効にして、R ソリューションのエンタープライズ開発の障壁を低く、R 言語の詳細とデータベースの統合を実現する革新的な機能も提供します。 これらの技術革新には、オープン ソースと Microsoft が開発した独自のコンポーネントの両方が含まれます。


SQL Server との統合の主な目標では、データを安全に管理する間に、R でのパフォーマンスの向上およびスケーラビリティを提供します。 この目標達成に向けたは、SQL Server の R のサービスは、統合 Windows 認証と SQL ログインのパスワード ベースの両方をサポートするマルチ プロセスのインフラストラクチャを提供します。 

+ [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] スケーラ パッケージと R のタスクを並列に実行する機能と共に、R の基本配布を提供します。
+ SQL Server の新しいコンポーネントは、外部のスクリプトを実行するため、セキュリティで保護された、高性能なフレームワークを提供します。
+ R のタスクは、セキュリティと管理容易性を提供する、SQL Server プロセス外で実行します。
+ [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] R のすべてのプロセスのセキュリティを管理します。 

既存の R コードを最適化して、これらの機能強化を活用するために、このセクションのトピックでは、新しいアーキテクチャの詳細について説明します。 によるデータの処理と分析を処理する方法について理解して [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], 、データの取り込み方法、特徴エンジニア リングを最も効率的に実行する方法と結果を処理する方法に関する適切な選択を行うことができます。
 

## このセクションの内容
+ [R の相互運用性](../../advanced-analytics/r-services/r-interoperability-in-sql-server-r-services.md)
+ [R Services 用 SQL Server の新しいコンポーネント](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r-services.md)
+ [セキュリティの概要](../../advanced-analytics/r-services/security-overview-sql-server-r-services.md)

## 参照
[R Services チュートリアル](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)
