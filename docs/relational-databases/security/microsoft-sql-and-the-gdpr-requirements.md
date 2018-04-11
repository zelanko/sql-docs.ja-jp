---
title: Microsoft SQL と GDPR の要件 |Microsoft ドキュメント
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.reviewer: ''
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: article
caps.latest.revision: 2
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 228cc003bfdd61bd0ead16e34810e52caf143438
ms.sourcegitcommit: 094c46e7fa6de44735ed0040c65a40ec3d951b75
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="guide-to-enhancing-privacy-and-addressing-gdpr-requirements-with-the-microsoft-sql-platform"></a>Microsoft SQL プラットフォームでのプライバシーの強化と GDPR 要件への対応に関するガイド
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

## <a name="summary"></a>[概要]
2018 年 5 月 25 日、プライバシー権利、セキュリティ、およびコンプライアンスに対する新しいグローバル制限を設定するヨーロッパのプライバシー法が発効します。 General Data Protection Regulation (GDPR) は、根本的に、個人のプライバシー権利を保護して有効にし、個々の選択を考慮しながら個人データを管理して保護する方法を管理する厳格なグローバル プライバシー要件を確立することに関係するものです。 

GDPR の対象となる Microsoft SQL のお客様は、管理対象がクラウド ベースのデータベースまたはオンプレミスのデータベースのどちらか一方か両方かに関わらず、データベース システム内の該当データが GDPR の原則に従って適切に処理および保護されていることを確認する必要があります。 つまり、お客様の多くが、特に GDPR で規定されているデータ処理のセキュリティにおいて、データベース管理およびデータ処理の手順を確認または変更する必要があります。

Microsoft SQL ベースのテクノロジでは、データへのリスクを軽減し、データベース レベル以上でデータの保護と管理を向上させるのに役立つ多くの組み込みセキュリティ機能が提供されています。 このホワイト ペーパーではこれらの機能を検証し、データのプライバシーに関する GDPR の目標を達成するための、 Microsoft SQL を使用した Microsoft 独自のアプローチの一部を紹介します。
   
  
**作成者:** Ronit Reger

**技術レビュー担当者:** Conor Cunningham、Joachim Hammer、Shai Kariv、Julie Koesmarno、Alice Kupcik、Ron Matchoro、Gilad Mittelman、Dan Rediske、Tomer Weisberg 
  
**公開日:** 2017 年 5 月  
  
**対象:** SQL Server (全バージョン)、Azure SQL Database、Azure SQL Data Warehouse、Analytics Platform System 
  
ドキュメントを読むには、「[Guide to enhancing privacy and addressing GDPR requirements with the Microsoft SQL platform (Microsoft SQL プラットフォームでのプライバシーの強化と GDPR 要件への対応に関するガイド)](http://download.microsoft.com/download/4/9/4/4948194B-A613-49ED-90A5-5144313549AB/microsoft-sql-and-the-gdpr.pdf)」をダウンロードしてください。   
