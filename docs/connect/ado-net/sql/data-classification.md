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
ms.openlocfilehash: b53e71c4c302145af14c1f2e37f30fe0e3c8f8e2
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725723"
---
# <a name="data-discovery-and-classification-in-sqlclient"></a>SqlClient でのデータの検出と分類

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

[データの検出と分類](../../../relational-databases/security/sql-data-discovery-and-classification.md?view=sql-server-2017)は、データベース内の機密データの検出、分類、ラベル付けとレポート作成を行うための高度なサービスのセットです。 SqlClient では、基になるソースが機能をサポートしている場合に、読み取り専用のデータ検出と分類情報を公開する API が提供されています。 この情報には、SqlDataReader を使用してアクセスします。

このサンプル アプリケーションは、SqlDataReader のデータ分類プロパティにアクセスする方法を示しています。

[!code-csharp [SqlDataReader_DataDiscoveryAndClassification#1](~/../sqlclient/doc/samples/SqlDataReader_DataDiscoveryAndClassification.cs#1)]

**参照**  

 [SQL Server の機能と ADO.NET](sql-server-features-adonet.md)