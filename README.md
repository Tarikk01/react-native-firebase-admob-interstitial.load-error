# react-native-firebase-admob-interstitial.load-error
I am trying to place interstitialAd in my project but the interstitialAd.load(); is crashing the app. My AdMob config is fine ad Banner ads are working perfectly.

Used Plugin: @react-native-firebase/admob


import { Button, View } from 'react-native';
import { InterstitialAd, AdEventType, TestIds } from '@react-native-firebase/admob';

export default class InterstitialAdUnit extends React.Component {
    constructor(props) {
        super(props);
    }
    
    showInterstitialAd = () => {
        
        const interstitialAd = InterstitialAd.createForAdRequest(TestIds.INTERSTITIAL);
       
        interstitialAd.onAdEvent((type, error) => {           
            if (type === AdEventType.LOADED) {
                interstitialAd.show();
            }
        });
        
        interstitialAd.load();
    } 
    render() {
        return (
            <Button
                title="Show Interstitial"
                onPress={() => {
                    this.showInterstitialAd();
                }}
            />    
    )}
}
