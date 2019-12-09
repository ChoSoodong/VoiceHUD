# VoiceHUD
声音录制提示HUD
```
- (void)pauseRecord {
  [self.voiceRecordHUD pauseRecord];
}

- (void)resumeRecord {
  [self.voiceRecordHUD resaueRecord];
}

- (void)cancelRecord {
  WEAKSELF
  [self.voiceRecordHUD cancelRecordCompled:^(BOOL fnished) {
    __strong __typeof(weakSelf)strongSelf = weakSelf;
    strongSelf.voiceRecordHUD = nil;
  }];
}

#pragma mark - Voice Recording Helper Method
- (void)startRecord {
  DDLogDebug(@"Action - startRecord");
  [self.voiceRecordHUD startRecordingHUDAtView:self.view];
  
}

- (void)finishRecorded {
  DDLogDebug(@"Action - finishRecorded");
  WEAKSELF
  [self.voiceRecordHUD stopRecordCompled:^(BOOL fnished) {
    __strong __typeof(weakSelf)strongSelf = weakSelf;
    strongSelf.voiceRecordHUD = nil;
  }];
  
}


- (VoiceRecordHUD *)voiceRecordHUD {
  if (!_voiceRecordHUD) {
    _voiceRecordHUD = [[VoiceRecordHUD alloc] initWithFrame:CGRectMake(0, 0, 140, 140)];
  }
  return _voiceRecordHUD;
}



```
