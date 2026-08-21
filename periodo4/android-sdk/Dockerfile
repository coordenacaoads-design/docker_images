# Android Studio - 4o Periodo
# Android Studio e uma IDE grafica (e o emulador precisa de KVM/GUI, o que
# nao funciona bem dentro de um container comum). O equivalente
# containerizavel e o Android SDK Command-line Tools: permite compilar,
# testar e empacotar apps Android via linha de comando (gradle/sdkmanager),
# sem a IDE grafica e sem emulador.
FROM eclipse-temurin:17-jdk-jammy

LABEL description="Android SDK Command-line Tools (equivalente CLI ao Android Studio)"

ENV ANDROID_SDK_ROOT=/opt/android-sdk \
    CMDLINE_TOOLS_VERSION=11076708

RUN apt-get update && apt-get install -y --no-install-recommends \
    wget unzip \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir -p ${ANDROID_SDK_ROOT}/cmdline-tools \
    && wget -q https://dl.google.com/android/repository/commandlinetools-linux-${CMDLINE_TOOLS_VERSION}_latest.zip -O /tmp/cmdline-tools.zip \
    && unzip -q /tmp/cmdline-tools.zip -d ${ANDROID_SDK_ROOT}/cmdline-tools \
    && mv ${ANDROID_SDK_ROOT}/cmdline-tools/cmdline-tools ${ANDROID_SDK_ROOT}/cmdline-tools/latest \
    && rm /tmp/cmdline-tools.zip

ENV PATH="${ANDROID_SDK_ROOT}/cmdline-tools/latest/bin:${ANDROID_SDK_ROOT}/platform-tools:${PATH}"

RUN yes | sdkmanager --licenses > /dev/null \
    && sdkmanager "platform-tools" "platforms;android-34" "build-tools;34.0.0"

WORKDIR /workspace
CMD ["bash"]
