---
title: カスタム レポート アイテム | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- extending Reporting Services
- Reporting Services, extending
- custom report items
ms.assetid: 64dcaf2c-1af5-4937-8ff7-98f1ec3b367e
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 162ec67283142da27f3afb1aa4f591a232177ac3
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56017944"
---
# <a name="custom-report-items"></a>カスタム レポート アイテム
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は、包括的な API により、エンタープライズ レポートの作成とパブリッシュ、セキュリティとサブスクリプションの管理、およびレポート機能の拡張を行う一連の豊富なツールを備えています。 レポートは、レポート定義言語 (RDL) と呼ばれる XML ベースの言語を使用して定義されます。 RDL は、レイアウト、クエリ情報、およびレポートのアイテムの種類を説明する一連の命令を提供します。 RDL は、カスタム レポート アイテムを作成することによって拡張できます。 カスタム レポート アイテムは、実行時にレポート プロセッサによって呼び出される実行時コンポーネント、およびカスタム レポート アイテムをレポート デザイナーで使用できるようにするデザイン時コンポーネントで構成されています。  
  
 完全に実装されたカスタム レポート アイテムの例については、「[SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)」 (SQL Server Reporting Services の製品サンプル) を参照してください。  
  
## <a name="custom-report-item-scenarios"></a>カスタム レポート アイテムのシナリオ  
 開発者が開発したアプリケーションに [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を統合する場合、RDL ではネイティブでサポートされていない機能が必要になることがあります。 たとえば、マップ コントロール、横一覧、縦一覧、および再ピボット可能なマトリックスなどです。 こうした要件を満たすため、実行時カスタム レポート アイテム コンポーネントを開発し、アプリケーションと共に配布することができます。  
  
 ネイティブでサポートされていない機能の提供という目的以外にも、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に既に含まれているコントロールの代替バージョンを使用して、開発者が既存の機能を拡張する場合があります。 このシナリオでは、開発者は、実行時コンポーネント、デザイン時コンポーネント、および必要に応じて既存のレポート アイテムをカスタム レポート アイテムに変換するデザイン時レポート アイテム変換コンポーネントという 3 種類のコンポーネントを提供します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [カスタム レポート アイテムのアーキテクチャ](custom-report-item-architecture.md)  
 カスタム レポート アイテムを構成するコンポーネントについて説明します。  
  
 [カスタム レポート アイテムの実装要件](custom-report-item-implementation-requirements.md)  
 カスタム レポート アイテムを作成するための前提条件について説明します。  
  
 [カスタム レポート アイテムの実行時コンポーネントの作成](creating-a-custom-report-item-run-time-component.md)  
 カスタム レポート アイテムの実行時コンポーネントの作成方法について説明します。  
  
 [カスタム レポート アイテムのデザイン時コンポーネントの作成](creating-a-custom-report-item-design-time-component.md)  
 カスタム レポート アイテムのデザイン時コンポーネントの作成方法について説明します。  
  
 [方法: カスタム レポート アイテムを配置する](how-to-deploy-a-custom-report-item.md)  
 カスタム レポート アイテムの配置方法について説明します。  
  
 [カスタム レポート アイテムのクラス ライブラリ](custom-report-item-class-libraries.md)  
 `Microsoft.ReportDesigner` 名前空間のカスタム レポート アイテム インフラストラクチャのクラスと、マネージド ラッパー クラスについて説明します。  
  
## <a name="see-also"></a>参照  
 [テクニカル リファレンス (SSRS)](../technical-reference-ssrs.md)  
  
  
