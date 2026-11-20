
import React, { useState } from "react";
import {
  View,
  Text,
  TextInput,
  TouchableOpacity,
  ScrollView,
  StyleSheet,
  Alert,
} from "react-native";

type Role = "admin" | "siswa";
type Status = "Siap Diambil" | "Belum Siap";

type Transaction = {
  id: number;
  type: "Pengambilan" | "Pengembalian";
  quantity: number;
  className: string;
  time: string;
};

type Pickup = {
  id: number;
  quantity: number;
};

const INITIAL_CLASSES = ["X-A", "X-B", "X-C", "XI-A", "XI-B", "XII-A"];

export default function App() {
  const [role, setRole] = useState<Role | null>(null);
  const [className, setClassName] = useState("X-A");
  const [selectedClass, setSelectedClass] = useState("X-A");
  const [status, setStatus] = useState<Record<string, Status>>(
    Object.fromEntries(
      INITIAL_CLASSES.map((c) => [c, "Belum Siap"])
    ) as Record<string, Status>
  );

  const [pickups, setPickups] = useState<Record<string, Pickup[]>>({});
  const [history, setHistory] = useState<Transaction[]>([]);
  const [quantity, setQuantity] = useState("");
  const [classes] = useState(INITIAL_CLASSES);

  const outstanding = (name: string) =>
    (pickups[name] || []).reduce((sum, p) => sum + p.quantity, 0);

  const totalTaken = (name: string) =>
    history
      .filter((t) => t.className === name && t.type === "Pengambilan")
      .reduce((sum, t) => sum + t.quantity, 0);

  const totalReturned = (name: string) =>
    history
      .filter((t) => t.className === name && t.type === "Pengembalian")
      .reduce((sum, t) => sum + t.quantity, 0);

  const recordTransaction = (
    type: "Pengambilan" | "Pengembalian",
    name: string,
    amount: number
  ) => {
    const transaction: Transaction = {
      id: Date.now(),
      type,
      quantity: amount,
      className: name,
      time: new Date().toLocaleString("id-ID"),
    };

    setHistory((old) => [transaction, ...old]);
  };

  const changeStatus = (name: string) => {
    setStatus((old) => ({
      ...old,
      [name]:
        old[name] === "Siap Diambil"
          ? "Belum Siap"
          : "Siap Diambil",
    }));
  };

  const takeOmpreng = () => {
    const amount = Number(quantity);

    if (!Number.isInteger(amount) || amount <= 0) {
      Alert.alert("Jumlah tidak valid", "Masukkan jumlah bilangan bulat lebih dari 0.");
      return;
    }

    if (status[selectedClass] !== "Siap Diambil") {
      Alert.alert("Belum siap", "Kelas ini belum berstatus Siap Diambil.");
      return;
    }

    setPickups((old) => ({
      ...old,
      [selectedClass]: [
        ...(old[selectedClass] || []),
        { id: Date.now(), quantity: amount },
      ],
    }));

    recordTransaction("Pengambilan", selectedClass, amount);
    setQuantity("");
    Alert.alert("Berhasil", "Pengambilan ompreng berhasil dicatat.");
  };

  const returnOmpreng = () => {
    const amount = Number(quantity);
    const current = pickups[selectedClass] || [];
    const total = outstanding(selectedClass);

    if (!Number.isInteger(amount) || amount <= 0) {
      Alert.alert("Jumlah tidak valid", "Masukkan jumlah bilangan bulat lebih dari 0.");
      return;
    }

    if (amount > total) {
      Alert.alert(
        "Pengembalian ditolak",
        `Jumlah yang belum dikembalikan hanya ${total}.`
      );
      return;
    }

    let remaining = amount;
    const updated = current.map((pickup) => {
      if (remaining <= 0) return pickup;

      const returned = Math.min(pickup.quantity, remaining);
      remaining -= returned;

      return {
        ...pickup,
        quantity: pickup.quantity - returned,
      };
    }).filter((pickup) => pickup.quantity > 0);

    setPickups((old) => ({
      ...old,
      [selectedClass]: updated,
    }));

    recordTransaction("Pengembalian", selectedClass, amount);
    setQuantity("");
    Alert.alert("Berhasil", "Pengembalian ompreng berhasil dicatat.");
  };

  const logout = () => {
    setRole(null);
    setQuantity("");
  };

  const Button = ({
    label,
    onPress,
    color = "#2563eb",
  }: {
    label: string;
    onPress: () => void;
    color?: string;
  }) => (
    <TouchableOpacity
      style={[styles.button, { backgroundColor: color }]}
      onPress={onPress}
    >
      <Text style={styles.buttonText}>{label}</Text>
    </TouchableOpacity>
  );

  if (!role) {
    return (
      <View style={styles.container}>
        <Text style={styles.logo}>my MBG</Text>
        <Text style={styles.subtitle}>
          Sistem Pengelolaan Ompreng Sekolah
        </Text>

        <View style={styles.card}>
          <Text style={styles.heading}>Masuk sebagai</Text>
          <Button label="Admin / Guru Piket" onPress={() => setRole("admin")} />
          <Button
            label="Siswa / Ketua Kelas"
            color="#059669"
            onPress={() => setRole("siswa")}
          />
          <Text style={styles.note}>
            Mode demo: pilih peran untuk mencoba aplikasi.
          </Text>
        </View>
      </View>
    );
  }

  const visibleClass = role === "admin" ? selectedClass : className;

  return (
    <View style={styles.container}>
      <View style={styles.header}>
        <View>
          <Text style={styles.logo}>my MBG</Text>
          <Text style={styles.subtitle}>
            {role === "admin" ? "Panel Admin" : `Kelas ${className}`}
          </Text>
        </View>
        <TouchableOpacity onPress={logout}>
          <Text style={styles.logout}>Keluar</Text>
        </TouchableOpacity>
      </View>

      <ScrollView>
        {role === "admin" && (
          <View style={styles.card}>
            <Text style={styles.heading}>Pilih Kelas</Text>
            <View style={styles.classList}>
              {classes.map((item) => (
                <TouchableOpacity
                  key={item}
                  onPress={() => setSelectedClass(item)}
                  style={[
                    styles.classButton,
                    selectedClass === item && styles.activeClass,
                  ]}
                >
                  <Text
                    style={[
                      styles.classText,
                      selectedClass === item && styles.activeClassText,
                    ]}
                  >
                    {item}
                  </Text>
                </TouchableOpacity>
              ))}
            </View>
          </View>
        )}

        {role === "siswa" && (
          <View style={styles.card}>
            <Text style={styles.heading}>Pilih Kelas Demo</Text>
            <View style={styles.classList}>
              {classes.map((item) => (
                <TouchableOpacity
                  key={item}
                  onPress={() => setClassName(item)}
                  style={[
                    styles.classButton,
                    className === item && styles.activeClass,
                  ]}
                >
                  <Text
                    style={[
                      styles.classText,
                      className === item && styles.activeClassText,
                    ]}
                  >
                    {item}
                  </Text>
                </TouchableOpacity>
              ))}
            </View>
            <Text style={styles.note}>
              Pemilihan kelas ini hanya untuk simulasi.
            </Text>
          </View>
        )}

        <View style={styles.card}>
          <Text style={styles.heading}>Status MBG</Text>
          <Text
            style={[
              styles.status,
              {
                color:
                  status[visibleClass] === "Siap Diambil"
                    ? "#059669"
                    : "#dc2626",
              },
            ]}
          >
            {status[visibleClass]}
          </Text>

          {role === "admin" && (
            <Button
              label="Ubah Status"
              onPress={() => changeStatus(selectedClass)}
            />
          )}
        </View>

        <View style={styles.card}>
          <Text style={styles.heading}>Data Ompreng - {visibleClass}</Text>

          <View style={styles.stats}>
            <View style={styles.statBox}>
              <Text style={styles.statNumber}>
                {totalTaken(visibleClass)}
              </Text>
              <Text style={styles.statLabel}>Diambil</Text>
            </View>
            <View style={styles.statBox}>
              <Text style={styles.statNumber}>
                {totalReturned(visibleClass)}
              </Text>
              <Text style={styles.statLabel}>Dikembalikan</Text>
            </View>
            <View style={styles.statBox}>
              <Text style={styles.statNumber}>
                {outstanding(visibleClass)}
              </Text>
              <Text style={styles.statLabel}>Belum Kembali</Text>
            </View>
          </View>
        </View>

        {role === "admin" && (
          <View style={styles.card}>
            <Text style={styles.heading}>Transaksi Ompreng</Text>
            <TextInput
              style={styles.input}
              keyboardType="numeric"
              placeholder="Masukkan jumlah ompreng"
              value={quantity}
              onChangeText={setQuantity}
            />
            <Button label="Catat Pengambilan" onPress={takeOmpreng} />
            <Button
              label="Catat Pengembalian"
              color="#059669"
              onPress={returnOmpreng}
            />
          </View>
        )}

        <View style={styles.card}>
          <Text style={styles.heading}>Riwayat Transaksi</Text>
          {history.filter((t) =>
            role === "admin" ? t.className === selectedClass : t.className === className
          ).length === 0 ? (
            <Text style={styles.note}>Belum ada transaksi.</Text>
          ) : (
            history
              .filter((t) =>
                role === "admin"
                  ? t.className === selectedClass
                  : t.className === className
              )
              .map((item) => (
                <View key={item.id} style={styles.historyItem}>
                  <View>
                    <Text style={styles.historyTitle}>
                      {item.type} - {item.className}
                    </Text>
                    <Text style={styles.note}>{item.time}</Text>
                  </View>
                  <Text style={styles.historyQuantity}>
                    {item.quantity} buah
                  </Text>
                </View>
              ))
          )}
        </View>
      </ScrollView>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: "#f1f5f9",
    paddingTop: 55,
    paddingHorizontal: 18,
  },
  header: {
    flexDirection: "row",
    justifyContent: "space-between",
    alignItems: "center",
    marginBottom: 18,
  },
  logo: {
    fontSize: 30,
    fontWeight: "bold",
    color: "#2563eb",
  },
  subtitle: {
    color: "#64748b",
    marginTop: 3,
  },
  logout: {
    color: "#dc2626",
    fontWeight: "bold",
  },
  card: {
    backgroundColor: "#fff",
    padding: 17,
    borderRadius: 14,
    marginBottom: 14,
  },
  heading: {
    fontSize: 18,
    fontWeight: "bold",
    color: "#1e293b",
    marginBottom: 13,
  },
  button: {
    padding: 14,
    borderRadius: 9,
    alignItems: "center",
    marginTop: 9,
  },
  buttonText: {
    color: "#fff",
    fontWeight: "bold",
  },
  note: {
    fontSize: 12,
    color: "#64748b",
    marginTop: 7,
  },
  status: {
    fontSize: 20,
    fontWeight: "bold",
    marginBottom: 5,
  },
  classList: {
    flexDirection: "row",
    flexWrap: "wrap",
    gap: 8,
  },
  classButton: {
    paddingVertical: 9,
    paddingHorizontal: 14,
    borderRadius: 8,
    backgroundColor: "#e2e8f0",
  },
  activeClass: {
    backgroundColor: "#2563eb",
  },
  classText: {
    color: "#334155",
    fontWeight: "600",
  },
  activeClassText: {
    color: "#fff",
  },
  stats: {
    flexDirection: "row",
    justifyContent: "space-between",
    gap: 7,
  },
  statBox: {
    flex: 1,
    backgroundColor: "#eff6ff",
    padding: 10,
    borderRadius: 9,
    alignItems: "center",
  },
  statNumber: {
    fontSize: 21,
    fontWeight: "bold",
    color: "#2563eb",
  },
  statLabel: {
    fontSize: 11,
    color: "#64748b",
    textAlign: "center",
  },
  input: {
    backgroundColor: "#f8fafc",
    borderWidth: 1,
    borderColor: "#cbd5e1",
    padding: 13,
    borderRadius: 9,
  },
  historyItem: {
    flexDirection: "row",
    justifyContent: "space-between",
    alignItems: "center",
    borderBottomWidth: 1,
    borderBottomColor: "#e2e8f0",
    paddingVertical: 12,
  },
  historyTitle: {
    fontWeight: "600",
    color: "#334155",
  },
  historyQuantity: {
    fontWeight: "bold",
    color: "#2563eb",
  },
});
