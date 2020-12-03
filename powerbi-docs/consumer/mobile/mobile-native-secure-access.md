---
title: デバイス ネイティブ ID で Power BI のデータを保護する
description: 自分の Power BI データにアクセスする前に追加 ID が必要になるように、ご利用の iOS および Android アプリを構成する方法について学習します
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 04/07/2020
ms.openlocfilehash: 9ca31aa16d74ab89b9af374244d2696f77dedac6
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413060"
---
# <a name="protect-power-bi-app-with-face-id-touch-id-passcode-or-biometric-data"></a>Face ID、Touch ID、パスコード、または生体認証データで Power BI アプリを保護する 

多くの場合、Power BI で管理されているデータは社外秘であり、保護され、承認されたユーザーのみによってアクセスされる必要があります。 

iOS や Android 用の Power BI アプリでは、追加 ID を構成することによって、ご利用のデータを保護することができます。 その後、アプリが起動するか、フォアグラウンドになるたびに、ID が必要になります。 iOS では、これは、Face ID、Touch ID、またはパスコードを入力することを意味します。 Android では、生体認証データ (指紋 ID) を入力することを意味します。

適用対象:

| ![iPhone](./media/mobile-native-secure-access/ios-logo-40-px.png) | ![iPad](./media/mobile-native-secure-access/ios-logo-40-px.png) | ![Android フォン](././media/mobile-native-secure-access/android-logo-40-px.png) | ![Android タブレット](././media/mobile-native-secure-access/android-logo-40-px.png) |
|:--- |:--- |:--- |:--- |
|iPhones |iPad |Android フォン |Android タブレット |

## <a name="turn-on-face-id-touch-id-or-passcode-on-ios"></a>iOS で Face ID、Touch ID、またはパスコードをオンにする

iOS 用 Power BI モバイル アプリで追加 ID を使用するには、 **[プライバシーとセキュリティ]** の下でアプリ設定に移動します。 Face ID、Touch ID、またはパスコードをオンにするオプションが表示されます。 表示されるオプションは、ご利用のデバイスの機能によって異なります。

![Power BI iOS のアプリ設定ページ](./media/mobile-native-secure-access/mobile-ios-native-secured-setting.png)

この設定をオンにすると、アプリを起動するか、フォアグラウンドにするたびに、アプリにアクセスできるようになる前に ID の入力が求められます。

入力を求められる ID の種類は、ご利用のデバイスの機能によって異なります。 ご利用のデバイスで Face ID がサポートされる場合、Face ID を使用する必要があります。 Touch ID がサポートされる場合は、Touch ID を使用する必要があります。 どちらもサポートされない場合は、パスコードを指定する必要があります。 以下の画像は、Face ID 認証画面を示しています。

![Power BI iOS の Face ID](./media/mobile-native-secure-access/mobile-ios-native-secured-faceid.png)

## <a name="turn-on-biometric-data-fingerprint-id-on-android"></a>Android で生体認証データ (指紋 ID) をオンにする

Android 用 Power BI モバイル アプリで追加 ID を使用するには、 **[プライバシーとセキュリティ]** の下でアプリ設定に移動します。 生体認証データをオンにするオプションが表示されます。

![Power BI Android アプリの設定ページ](./media/mobile-native-secure-access/mobile-android-native-secured-setting.png)

この設定をオンにすると、アプリを起動するか、フォアグラウンドにするたびに、アプリにアクセスできるようになる前に生体認証データ (指紋 ID) の入力が求められます。

以下の画像は指紋認証画面を示しています。

![スクリーンショットには、Android フォンで追加 ID が必要であるというメッセージが表示されています。](./media/mobile-native-secure-access/mobile-android-native-secured-fingerprint-id.png)

>[!NOTE]
>モバイル アプリの [Require Biometric Authentification]\(生体認証が必要\) 設定を使用できるようにするには、まず、Android デバイスで生体認証を設定する必要があります。 デバイスで生体認証がサポートされていない場合は、このモバイル アプリ設定を使用して、Power BI データへのアクセスをセキュリティで保護することはできません。
>
>管理者がモバイル アプリの[セキュリティで保護されたアクセスをリモートでオンにした](#mdm-enforcement-of-secure-access-to-your-power-bi-mobile-app)場合、アプリにアクセスするためにデバイスに生体認証を設定する必要があります (まだそのようにしていない場合)。 デバイスで生体認証がサポートされていない場合、リモート設定による影響はありません。 モバイル アプリへのアクセスは、セキュリティで保護されていないままになります。

## <a name="mdm-enforcement-of-secure-access-to-your-power-bi-mobile-app"></a>Power BI モバイル アプリへのセキュリティで保護されたアクセスの MDM による強制。

一部の組織では、セキュリティ ポリシーとコンプライアンス要件があり、ビジネス上の機密データにアクセスするには、追加 ID を強制する必要があります。

これをサポートする場合、Power BI モバイル アプリを使用すると、管理者は Microsoft Intune やその他のモバイル デバイス管理 (MDM) ソリューションからアプリ構成設定をプッシュすることで、モバイル アプリのセキュリティで保護されたアクセス設定を制御できます。 管理者はアプリ保護ポリシーを使用して、すべてのユーザーまたはユーザーのグループに対してこの設定をオンにすることができます。 詳細については、[MDM を使用する Power BI モバイル アプリのリモートでの構成](mobile-app-configuration.md#data-protection-settings-ios-and-android)に関する記述を参照してください。

## <a name="next-steps"></a>次のステップ
* [MDM を使用してリモートで Power BI モバイル アプリを構成する](mobile-app-configuration.md)
