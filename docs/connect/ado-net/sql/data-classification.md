---
title: SqlClient でのデータの検出と分類
description: SQL Server データベースでデータ分類がサポートされているかどうかをチェックする方法、および SqlDataReader オブジェクトを介してデータ分類情報にアクセスする方法について説明します。
ms.date: 06/15/2020
dev_langs:
- csharp
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: johnnypham
ms.author: v-jopha
ms.reviewer: ''
ms.openlocfilehash: 27b9c232fe785d3c016848f3bb952236b8e7cd75
ms.sourcegitcommit: 6b3569977b034554883a94d73d1c4df6e2f74fe2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2020
ms.locfileid: "85110157"
---
# <a name="data-discovery-and-classification-in-sqlclient"></a>SqlClient でのデータの検出と分類

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

[データの検出と分類](https://docs.microsoft.com/sql/relational-databases/security/sql-data-discovery-and-classification?view=sql-server-2017)は、データベース内の機密データの検出、分類、ラベル付けとレポート作成を行うための高度なサービスのセットです。 SqlClient では、基になるソースが機能をサポートしている場合に、読み取り専用のデータ検出と分類情報を公開する API が提供されています。 この情報には、SqlDataReader を使用してアクセスします。

このサンプル アプリケーションは、SqlDataReader のデータ分類プロパティにアクセスする方法を示しています。

[!code-csharp [SqlDataReader_DataDiscoveryAndClassification#1](~/../sqlclient/doc/samples/SqlDataReader_DataDiscoveryAndClassification.cs#1)]

**参照**  

 [SQL Server の機能と ADO.NET](sql-server-features-adonet.md)   
