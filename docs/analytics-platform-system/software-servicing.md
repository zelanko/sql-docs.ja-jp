---
title: ソフトウェア (Analytics Platform System) のサービス
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cec4d924-c88f-470c-84bb-0af3e21aabf1
caps.latest.revision: 33
ms.openlocfilehash: 8bddf00569ad4c5e5c78e801399b589a9f6d5f42
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="software-servicing"></a>ソフトウェアのサービス
このセクションでは、サービスの Analytics Platform System アプライアンスには、WSUS および Analytics Platform System の修正プログラムを含むの要件、ソフトウェアをまとめたものです。  
  
## <a name="Basics"></a>ソフトウェアのサービスの基礎  
**WSUS:** Analytics Platform System アプライアンスは、Windows Server Update Services (WSUS) から更新プログラムを受信するように構成する必要があります。 これらの更新プログラムには、アプライアンス ソフトウェアの重要な変更が含まれます。 構成後多数の更新プログラムは自動的にインストールされ、実践的な管理は不要します。 通常、WSUS 更新プログラムが中に構成、 [Windows Server Update Services の構成&#40;WSUS&#41; &#40;Analytics Platform System&#41; ](configure-windows-server-update-services-wsus.md)新しいアプライアンス セットアップ中に手順を実行します。 それ以外の場合は、この構成手順を後で実行することができます。 WSUS については、次を参照してください。、 [WSUS web サイト ガイド](http://go.microsoft.com/fwlink/?LinkId=202417)です。  
  
**修正プログラム:**さらに、Analytics Platform System の修正プログラムを適用する必要があります。 A*修正プログラム*分析プラットフォーム システム ソフトウェアの問題を解決するのには、特定の顧客に対して作成されたソフトウェアの更新します。 各修正プログラムは、顧客固有の問題の修正プログラムをインストールする実行可能ファイルです。 各修正プログラムには、Windows、SQL Server、および Analytics Platform System を超えて繰り返し発生するすべての以前にリリースされたソフトウェア更新プログラムも含まれています。 修正プログラムをインストールする場合は、Microsoft サポートが修正プログラムと指示を提供するは。  
  
**更新プログラムのスコープ:**分析プラットフォーム システムに修正プログラムまたはサービス パックを適用する必要がありますをオフラインに全体のアプライアンスです。 つまり、PDW と HDInsight の両方の地域に影響があります。  
  
**SSIS 変換先アダプターとクライアント ツール:** SSIS 変換先アダプター MSI への変更を含む、修正プログラムを適用するときにまたは MSI ファイルは更新のクライアント ツールの msi ファイルを**C:\PDWINST\ClientTools**コントロールのノード上のディレクトリ。 修正プログラムでは、コンポーネントは自動的には、更新された MSI ファイルからインストールされません。 これらのコンポーネントを更新するには、顧客必要があります、コンポーネントの以前のバージョンをアンインストールし、更新された MSI ファイルから新しいバージョンをインストールします。 SSIS 変換先アダプター MSI への変更を含む、修正プログラムのアンインストール時に、またはクライアント ツールの MSI、それらのコンポーネントの MSI ファイルは以前のバージョンに戻されます。 これらコンポーネントを以前のバージョンに戻すには、顧客は、コンポーネントの既存の (最新) バージョンをアンインストールし、元に戻された MSI ファイルからの古いバージョンを再インストールする必要があります。  
  
## <a name="software-servicing-topics"></a>ソフトウェアのサービスに関するトピック  
次のトピックでは、アプライアンス上でソフトウェアのサービスを管理する方法について説明します。  
  
-   [ダウンロードして Microsoft 更新プログラムを適用して&#40;分析プラットフォーム システム&#41;](download-and-apply-microsoft-updates.md)  
  
-   [Microsoft 更新プログラムのアンインストール&#40;分析プラットフォーム システム&#41;](uninstall-microsoft-updates.md)  
  
-   [分析プラットフォーム システムの修正プログラム適用&#40;分析プラットフォーム システム&#41;](apply-analytics-platform-system-hotfixes.md)  
  
-   [分析プラットフォーム システムの修正プログラムをアンインストール&#40;分析プラットフォーム システム&#41;](uninstall-analytics-platform-system-hotfixes.md)  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
