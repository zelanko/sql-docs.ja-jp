---
title: サーバーのプロパティ ([その他のサーバーの設定] ページ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.miscserversettings.f1
ms.assetid: b170c066-30cd-42dd-8d34-aa129ea09551
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d726e1e79b1a3e24aea074c0821e1f8773b233c5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62809332"
---
# <a name="server-properties-misc-server-settings-page"></a>[サーバーのプロパティ] ([その他のサーバーの設定] ページ)
  このページを使用すると、サーバーの設定を表示したり、変更したりできます。  
  
## <a name="options"></a>オプション  
 **ユーザーの既定の言語**  
 新しく作成するすべてのログインの既定の言語を指定します。  
  
 **トリガーによる他のトリガーの起動を許可する**  
 トリガーによって別のトリガーを起動するアクションを実行するかどうかを制御します。 このオプションをオフにすると、トリガーは別のトリガーによって起動されません。 このオプションをオンにすると、トリガーは最大 32 レベルまで別のトリガーによって起動されます。  
  
 **クエリガバナーを使用して実行時間の長いクエリを防止する**  
 クエリを実行する最大時間を指定します。 クエリ コストとは、特定のハードウェア構成でクエリを実行するために必要とされる予測所要時間を秒単位で表したものです。 既定では、クエリ カバナはオフになっており、すべてのクエリは実行が許可されています。 このオプションをオンにする場合は、下のテキスト ボックスに時間制限を入力する必要があります。 0 以外の正の値を指定すると、クエリ ガバナーは、見積コストがこの値を超えるクエリの実行を許可しません。  
  
 **2桁の年を次の間隔になるように解釈する**  
 2 桁の年の値を解釈するために 100 年の日付範囲を指定します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、2桁の日付値を解釈し、指定された範囲内にあるその数字で終わる年を参照します。  
  
 右のボックスで終了年を設定します。 終了年が保存されると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の左のボックスに自動的に開始年が入力されます。  
  
 **構成された値**  
 このペインの各オプションに構成されている値を表示します。 これらの値を変更した場合は、 **[実行中の値]** をクリックして、変更後の値が反映されているかどうかを確認してください。 値が反映されていない場合は、先に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを再指定する必要があります。  
  
 **実行中の値**  
 このペイン上のオプションの、現在実行中の値を表示します。 これらの値は読み取り専用です。  
  
## <a name="see-also"></a>参照  
 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
  
