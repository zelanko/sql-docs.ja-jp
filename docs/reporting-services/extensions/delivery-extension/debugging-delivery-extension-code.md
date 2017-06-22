---
title: "配信拡張機能コードのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- delivery extensions [Reporting Services], debugging
- debugging delivery extensions [Reporting Services]
- troubleshooting [Reporting Services], delivery extensions
ms.assetid: a7d959da-5005-4a50-aca7-2cef36aa9947
caps.latest.revision: 35
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: d3e683887f02436ad948b6a6aedb64ef749a7547
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="debugging-delivery-extension-code"></a>配信拡張機能のコードのデバッグ
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]するのに役立ついくつかのデバッグ ツール、配信拡張機能のコードを分析エラーを探すことを示します。 最適なデバッグ ツールは、使用する目的によって異なります。 この例では [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)]を使用します。  
  
#### <a name="to-debug-your-delivery-extension-code"></a>配信拡張機能のコードをデバッグするには  
  
1.  起動[!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)]し、配信拡張機能プロジェクトを開きます。  
  
2.  プロジェクトをビルドし、配信拡張機能アセンブリとその .pdb ファイルをレポート サーバーとレポート マネージャーに配置します。 展開の詳細については、次を参照してください。[配信拡張機能の配置](../../../reporting-services/extensions/delivery-extension/deploying-a-delivery-extension.md)です。  
  
3.  サブスクリプション ユーザー インターフェイスを記述してレポート マネージャーを拡張した場合は、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] で配信拡張機能のコードを開いたまま、Internet Explorer を開いてレポート マネージャーに移動します。 レポート マネージャーのサブスクリプション ユーザー インターフェイスを配置していない場合は、クライアント アプリケーションを開き、そこから SOAP API を使用して配信拡張機能を呼び出します。  
  
4.  [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] および配信拡張機能のプロジェクトに移動し、コードにブレーク ポイントを設定します。  
  
5.  配信拡張機能プロジェクト ウィンドウをアクティブなままで、をクリックして**プロセスにアタッチする**上、**デバッグ**メニュー。  
  
     **プロセスにアタッチする**ダイアログ ボックスが開きます。  
  
6.  、プロセスの一覧から aspnet_wp.exe プロセス (または、アプリケーションが IIS 6.0 に展開されている場合は w3wp.exe) を選択し、をクリックして**アタッチ**です。  
  
7.  配信拡張機能を使用して新しいサブスクリプションを定義します。 通常は、レポート マネージャーまたは SOAP API を使用します。 これにより、デバッガーが呼び出され、ブレーク ポイントに対応するコードが実行されます。  
  
8.  使用してコードをステップスルー、 **F11**キー。 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] を使用したデバッグの詳細については、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] のマニュアルを参照してください。  
  
## <a name="see-also"></a>参照  
 [Implementing a Delivery Extension](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
